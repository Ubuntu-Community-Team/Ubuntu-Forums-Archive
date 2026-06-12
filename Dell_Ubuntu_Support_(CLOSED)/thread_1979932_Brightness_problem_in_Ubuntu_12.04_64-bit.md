---
title: "Brightness problem in Ubuntu 12.04 64-bit"
date: 2012-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ksprasad on 2012-05-14
Hi All,
 
In my Dell xps laptop, brightness is not getting changed. Pressing the on-board key or brightness setting will increase/decrease the brightness bar in top corner. But no effect is seen on the screen. Brightness remains same and after a reboot the brightness bar resets to maximum.
 
I have installed Bumblebee to activate Nvidia. But this wont matter I guess as this issue is observed even before installing bumblebee.
 
Any suggestions?
 
 
 
Specs:
 
Ubuntu 12.04 LTS 64-bit
4 BG ram
i5 480M processor
Nvidia 420M 1GB graphics card.
 
 
 
Thanks,
ksprasad

---

### Post by ksprasad on 2012-05-15
Hi,

I tried lot of solutions suggested by various people. None of them worked for me. When I used the function keys, the value in '/sys/class/backlight/acpi_video0/brightness' was getting changed but screen brightness was not changing.

Finally got it solved with following method:

```
xrandr --output LVDS1 --brightness 0.5
```

Got it from the following thread:

[http://ubuntuforums.org/showthread.php?t=1907928&page=5](http://ubuntuforums.org/showthread.php?t=1907928&page=5)

Regards,
ksprasad

---

### Post by abugabbu on 2012-08-10
> **ksprasad said:**
> Hi,

I tried lot of solutions suggested by various people. None of them worked for me. When I used the function keys, the value in '/sys/class/backlight/acpi_video0/brightness' was getting changed but screen brightness was not changing.

Finally got it solved with following method:

```
xrandr --output LVDS1 --brightness 0.5
```Got it from the following thread:

[http://ubuntuforums.org/showthread.php?t=1907928&page=5](http://ubuntuforums.org/showthread.php?t=1907928&page=5)

Regards,
ksprasad
Hi, but the actual solution is not that. Its a great mess.

When you try the xrandr --brigntness 0.5 to LVDS1, it will just decrease the Contrast value and will not save the power that you were expecting on the Ubuntu. You need to fix that permanently. So, hope to get that on on the Linux kernel or you can get help from here: 
> [http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

With the solution mentioned on above link your (FN + Brightness UP/DOWN) both shall work on a single restart.
Enjoy

---

### Post by ksprasad on 2012-09-19
Hi,
 
Now only i saw your reply. Thanks for the suggestion. I didn't know that it will decrease only contrast. But earlier the screen was too bright and it was difficult to sit more than 15 mins and that way it worked for me. :)
 
And off course i already tried the solution you mentioned and it did not work :( . May be after few kernel updates it might get resolved. Have to see.
 
Regards,
ksprasad

---

### Post by magtrask on 2012-09-21
I use an HP Pavilion dm3 and had the same problem. Easy fix with the link given above:
[HTML][http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)[/HTML]
Thanks!

---

### Post by hjns62 on 2013-03-05
[http://www.techjail.net/solved-brigh...-pangolin.html]("http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html")

Thanks for the link, ksprasad.It corrects my Ubuntu 12.04 brightness control on a HP DV6 pavillion with Intel/ATI hybrid... Just perfect. Many thanks, again.

---

### Post by rishabharora46 on 2013-07-14
Hey I have found this : [http://bit.ly/12pe6dp](http://bit.ly/12pe6dp). Go to this link to adjust brightness this worked for me..

---

### Post by TheDavidJohnson on 2013-08-12
> **abugabbu said:**
> Hi, but the actual solution is not that. Its a great mess.

When you try the xrandr --brigntness 0.5 to LVDS1, it will just decrease the Contrast value and will not save the power that you were expecting on the Ubuntu. You need to fix that permanently. So, hope to get that on on the Linux kernel or you can get help from here: 

[http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

With the solution mentioned on above link your (FN + Brightness UP/DOWN) both shall work on a single restart.
Enjoy

Thanks for this! I've tried several other solutions in the past, but this enabled my laptop's buttons to finally control screen brightness. Appreciate your help!

---

### Post by jlh68 on 2013-08-23
I tried the Techjail procedure and nothing happens and I don't even get the birghtness applet.  So no brightness control and no appalet when pressing Fn right arrow or Fn left arrow (brightness down or up).
This is on the Acer Aspire One 725 netbook (64-bit OS)
How about another fix?

---

### Post by TheDavidJohnson on 2013-08-28
No sooner had I gotten this working a couple of weeks ago in 12.04 and I decided today to blow up my Precise install and switch to 13.04. I can confirm that the Techjail procedure does not work (on my Gateway NV57H44u at least) in 13.04 64-bit.

So, after some digging around I came across this solution instead. Using the following:

[FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

[/FONT]to replace the default line (which just ends in "quiet splash") in grub did the trick for me! I've read that it may work on other Ubuntu versions as well. Worth a shot!

---

### Post by qhaz on 2013-09-07
I am faced with the same problem of being unable to adjust the backlight on my HP Pavilion 15z Laptop (Graphics - AMD Radeon HD 8400G).
I've tried all the methods suggested in these posts and various others.  Has anyone had any success with this particular HP Pavilion model?  Open to all suggestions.

---

### Post by mortramalt on 2014-02-21
I tried the solution below, and the result was that my desktop loaded to the wallpaper and remained frozen, so much so that I couldn't access virtual terminals with Ctrl + Alt + F1.  Had to remove the setting and still can't set the brightness.  This is on a Dell Inspiron 17 model 3737, Intel integrated 4400 graphics.

> **TheDavidJohnson said:**
> No sooner had I gotten this working a couple of weeks ago in 12.04 and I decided today to blow up my Precise install and switch to 13.04. I can confirm that the Techjail procedure does not work (on my Gateway NV57H44u at least) in 13.04 64-bit.

So, after some digging around I came across this solution instead. Using the following:

[FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

[/FONT]to replace the default line (which just ends in "quiet splash") in grub did the trick for me! I've read that it may work on other Ubuntu versions as well. Worth a shot!

---

### Post by jlh68 on 2014-02-22
I still do not have a solution to changing the screen brightness on this netbook (Acer One 725).  When I use the Fn key and the brightness keys the upper right indicator of blrightnes goes crazy without any change in the screen.  It is obvious from all the other comments that this is an OS problem rather than a hardware problem.  I wonder shy the Ubuntu team doesn't make a working patch for the problem?

---

### Post by albert15 on 2014-03-16
Supreme solution! I was about 3 years without the possibility to change the brightness of my laptop. Terminal commands rules!

In addition, if "xrandr" is written alone it returns all the screen specifications and its names.

Abraço
albert

---

### Post by Kiran_Nambiar on 2014-06-08
thanx :-)

---

### Post by cptjaq on 2014-07-22
> **TheDavidJohnson said:**
> No sooner had I gotten this working a couple of weeks ago in 12.04 and I decided today to blow up my Precise install and switch to 13.04. I can confirm that the Techjail procedure does not work (on my Gateway NV57H44u at least) in 13.04 64-bit.

So, after some digging around I came across this solution instead. Using the following:

[FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

[/FONT]to replace the default line (which just ends in "quiet splash") in grub did the trick for me! I've read that it may work on other Ubuntu versions as well. Worth a shot!

I have an ASUS X401U running 12.04 and this solved my problem perfectly.

---

