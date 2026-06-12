---
title: "Strange windows borders after upgrade to 8.10"
date: 2008-11-08
forum: Desktop Environments
---

### Post by B3rt on 2008-11-08
Since I upgraded to version 8.10 i am experiencing strange borders on my windows.

I made some screenshots to explain it better, see your self, watch the top of each window in the screenshot:

[img]http://www.seelen.nu/files/ubuntu/screenshot1.png[/img]
[img]http://www.seelen.nu/files/ubuntu/screenshot2.png[/img]
[img]http://www.seelen.nu/files/ubuntu/screenshot4.png[/img]

I am using version 8.10 (latest) with an nvidia card, also using compiz.
This problem immediately appeared after the update from 8.04 to 8.10 was completed, in 8.04 all was working perfectly, no strange borders. 

Does anyone have an idea what is causing this but more important how to fix this?

---

### Post by eaidoido on 2008-11-08
does this happen with emerald themes?

---

### Post by hictio on 2008-11-08
Oh, man! I thought I was the only one... Yes, I have seen them too, right after installing/ enabling the NVIDIA driver, but, since I use Emerald (and the window borders don't get screwed with that window manager) I just kept going on.

[URL=http://img411.imageshack.us/my.php?image=windowborderprobs00fg7.png]
[IMG]http://img411.imageshack.us/img411/5369/windowborderprobs00fg7.th.png[/IMG]
[/URL]

I have a GeForce 7000M (rev a2) on a Compaq F700 laptop.

---

### Post by jedimasterk on 2008-11-08
This should have never been released this way. I wonder if Nvidia finds Windows 7 and MacOSX Snow Leopard drivers to be more of a priority over Gnu/Linux. Funny how this is happening now, right before these two releases. I would love to see Windows 7 coming out with this bug as well, on their windows borders.

---

### Post by B3rt on 2008-11-09
> **eaidoido said:**
> does this happen with emerald themes?

I use the default theme "human" of ubuntu, Emerald is not installed.
But is there a solution for this problem?

On my work I also use 8.10 with an nvidia card, i doubt now if i also have this problem on that machine. If i remember correctly my pc on my work does not have this problem, but i am not sure about that.

Who knows a solution?

---

### Post by hictio on 2008-11-09
On Emerald does not happen, I'm using [Human Tiger](http://gnome-look.org/content/show.php/Human+Tiger?content=69772), and used the default theme tha Emerald loads if there is not a single one installed, and the window border problem does not happen.
At least, it didn't on my Compaq, with the NVIDIA drivers provided by Ubuntu for Intrepid installed and running.

---

### Post by B3rt on 2008-11-10
I installed Emerald and using the "human" theme, still no change. The borders are still messed up

Does nobody know how I can solve this?

---

### Post by alejandro.mc on 2008-11-12
I could really use some help with this too.. Emerald din't fix it for me neither..

Thanks!

---

### Post by B3rt on 2008-11-13
I also installed an older driver 173.14, this also does not help to solve it.

---

### Post by Pengwyn44 on 2008-11-13
You must not complain - my computer would not re-start at all!
Solution - don't upgrade, have a clean install.

---

### Post by hictio on 2008-11-13
> **Pengwyn44 said:**
> You must not complain - my computer would not re-start at all!
Solution - don't upgrade, have a clean install.

I don't understand your post, but, I did a clean install of Intrepid, and I had the window border problems too, but simply vanished when started using Emerald, see my posts above.

---

### Post by sharkster2007 on 2008-11-13
I have this problem too with the 173 and 177 Drivers, it seems to be down to Nvidia lets hope they soon make new drivers for ubuntu without this "window title bar" problem.

These are "closed source" drivers, the "open Source" ones currently only work in 2D, I know its a bummer :-(

---

### Post by Eddie Wilson on 2008-11-13
This problem is relegated to Nvidia only. I had the same problem and then upgraded to an Ati video card and I no longer have any problems. With Ati becoming more linux friendly they have just passed Nvidia for recommended hardware. This is only my opinion and also my observation.

---

### Post by alejandro.mc on 2008-11-14
I did a clean install and the window borders are still having problems.

Anyone??

---

### Post by hictio on 2008-11-14
> **Eddie Wilson said:**
> This problem is relegated to Nvidia only. I had the same problem and then upgraded to an Ati video card and I no longer have any problems. With Ati becoming more linux friendly they have just passed Nvidia for recommended hardware. This is only my opinion and also my observation.

Well, I don't know... I have a NVIDIA card (GeForce 7000M (rev a2)) and I don't have the problem, ir, actually, had it for just a few minutes.

> **alejandro.mc said:**
> I did a clean install and the window borders are still having problems.

Anyone??

What video card do you have?
Are using Compiz & Emerald?

---

### Post by jbysmith on 2008-11-14
I've had this issue with my nVidia card for the past several versions of the driver.  Think the last one that didn't have this quirk was.. 164? Something like that.

Anywho.  nVidia released the **beta** driver version 180.06 recently, today I think. 

Note the beta; make sure you're comfortable with installing/uninstalling the nVidia driver by hand, which is pretty easy mind you; stop GDM, run the install script, restart GDM, done. Being beta, it might cause new bugs, make your system burst into flames, turn Stallman into a Windows user, or other strange results.

That said, I've been using it for the past few hours with zero issues.  Not only am I getting a performance boost (I *think*, it could be in my head, haven't benchmarked anything) but the title bars are now working as they should. Seems to have fixed an odd minimize bug I'd get with a particular Wine app that I use too.

If you're not wanting to mess with a beta driver, I got around the quirk by switching to an Emerald theme for the window borders.  I also had to disable the fade/pulsing animations, or it could also cause corruptions.

---

### Post by Pengwyn44 on 2008-11-15
I took my own advice and did a clean install. No problems till I tried to install my Magicolor 2400W printer. The correct drivers were not there.
The printer worked fine in 8.04 so I have re-installed 8.04.
I'll try 8.10 again when the experts have removed the bugs.

---

### Post by blue13130 on 2008-11-16
> **jbysmith said:**
> ...I got around the quirk by switching to an Emerald theme for the window borders.  I also had to disable the fade/pulsing animations, or it could also cause corruptions.

I also was having some trouble with the window border in 8.10 with Nvidia card.  I switched to Emerald but still had some problems (for some reason Thunderbird acted up the most of all windows) but now that I disabled the fade/pulsing I haven't had any trouble.  Thanks!

---

### Post by jbysmith on 2008-11-20
> **blue13130 said:**
> I also was having some trouble with the window border in 8.10 with Nvidia card.  I switched to Emerald but still had some problems (for some reason Thunderbird acted up the most of all windows) but now that I disabled the fade/pulsing I haven't had any trouble.  Thanks!

No problem, it's just a bandaid solution for a buggy driver, but does the trick.  Personally the newer drivers are a better solution though, don't need to disable anything, and seems a bit faster too.

---

### Post by dhuff on 2008-11-20
While I'm sure the problem is with the nVidia drivers, I found that I didn't have to use Emerald to make this go away. I just had to *not* choose any of the "Human" themes. Other themes worked w/o issues.

That being said, I really like the Human themes and look forward to an updated nVidia driver so I can start using them again...

---

### Post by B3rt on 2008-11-20
I fixed the problem also, I Downloaded ta beta driver from the nvidia website (version 1.80) and installed it, after reloading the driver the problem is gone! I did not first remove the old 177 driver, I just installed the new beta driver. I also noticed a little performance boost in my overall performance.

Nvidia write in the release note of the driver:
- Fixed a regression that could result in window decoration corruption when running Compiz using Geforce 6 and 7 series GPUs.

You can download the driver yourself from here:
[http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk)

note: 
you have to install the driver manually, the drivers are NOT yet avaiable from the synaptic packages but they do fix the problem!
Installing is easy, just follow instructions given by jbysmith

---

### Post by tarsius4 on 2008-11-21
> While I'm sure the problem is with the nVidia drivers, I found that I didn't have to use Emerald to make this go away. I just had to not choose any of the "Human" themes. Other themes worked w/o issues.

Same here... I switched to a different theme (via System>Preferences>Appearance) and now the title bar problem is gone. Hopefully it will be fixed in the future.

---

