---
title: "Tank Game Dev Log #6: Camera Aim"
date: 2025-05-17
rank: 0
summary: Added mouse aim / camera aim
description: 
toc: true
readTime: true
autonumber: true
math: true
tags:
  - video-game
  - dev-log
  - TankGame
showTags: true
hideBackToTop: false
---
# Camera Aim

I want to be able to aim the gun while in the third person camera. Because normally turret doesn't have roll control, there is some constraint that the rotations should be in pitch & yaw rotation only.
I do this by:
1. raycast from the camera & obtain the hit-point
2. get a direction vector from the gun tor the hit-point
3. translate the direction into direction relative the the turret's transform (which may not have the same axis as the world due to inclined ground) using `transform.InverseTransformDirection(direction)`
4. calculate the pitch & yaw from the relative direction
5. tell the turret to rotate & gun to aim up/down based on the current pitch & yaw VS target pitch & yaw
6. add some min-max pitch constraint
7. viola!

<blockquote class="twitter-tweet" data-theme="dark"><p lang="en" dir="ltr">added third person mouse / camera aim!🎦<br>with pitch min-max limit<br>works on inclined ground too<br><br>tbh i found that you can translate the target vector to the turret&#39;s local vector and that made things way easier to work with<br><br>(i was trying to &quot;rotate&quot; the pitch and yaw) <a href="https://t.co/Qbw2rjGuU4">https://t.co/Qbw2rjGuU4</a> <a href="https://t.co/1Q77E7oEpl">pic.twitter.com/1Q77E7oEpl</a></p>&mdash; meisbkkkkkkk (@meisbk) <a href="https://twitter.com/meisbk/status/1923943226681197064?ref_src=twsrc%5Etfw">May 18, 2025</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


# Gallery

{{< image-gallery gallery_dir="/image/video-games/TankGame" show_image_title="false" >}}
