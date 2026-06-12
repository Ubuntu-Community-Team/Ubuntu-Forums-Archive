---
title: "Beryl Install Ubuntu Crashed"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by Toriacht on 2007-05-22
Hi,

I was trying to install Beryl following the instructions posted here:

[http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon](http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon)

Everything was fine until I restarted X after editing /etc/X11/xorg.conf in Step 3. My machine crashed and will not boot into Ubuntu any more. I get a screen similar to the Windows Blue Screen of Death telling me there is a problem with the xorg.conf file.

I can boot into the Recovery Mode but don't know what to do next!? Is there a step by step resource anywhere to help me recover?

Thanks,
Toriacht

---

### Post by ericallen on 2007-05-22
go to recovery mode and try 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Toriacht on 2007-05-22
Thanks for your reply Eric,

I used vi to edit the xorg.conf file from recovery mode. I had referenced an input device mentioned in the *howto* in the *ServerLayout* that was not installed on my machine. When i removed this my machine booted up fine.

Thanks again,
Toriacht

---

