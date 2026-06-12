---
title: "nvidia config not working"
date: 2006-06-23
forum: Desktop Environments
---

### Post by neighborlee on 2006-06-23
hi,
  I have a amd64 3200+ and nvidia 6800XT gpu.

  I just installed nvidia-glx and went to issue nvidia-glx-config enable, but it threw an error  something about X config has been altered and can not procede, and that I needed to run this one liner command with md5sum, - which I did and it went fine with no errors.

   I then redid the enable command above, and this time it worked with no errors of anykind.  I restarted and found that xorg.conf had been setup incorrectly.

   ONe terribly odd note is that  it was showing that I had a ATI card ??...if ubuntu is trying to convert us all to ATI its not working LOL

   soooooo..I saw in the error message that the ide BUS number was  1 :5:0 , whereas of course my system was expecting 1:0:0, so I changed it to that expected value and issued startx and I was into desktop.

  This may help you if you come across this error.

cheers
nl

---

