---
title: "Problems with AMD Radeon HD 7570M Graphics Card on Dell 14z 5423 Inspiron Ultrabook"
date: 2013-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by treeclimber on 2013-06-23
I'm having problems running Ubuntu on my Dell 14z 5423  Ultrabook with an Intel i7 processor.  It has Windows 7 on it and a wubi install of Ubuntu 12.10.  It has an AMD Radeon HD 7570M Graphics card and IntelR HD Graphics 4000 integrated.  If I run Ubuntu, it overheats every time and I have to shut it off.  I can't run it long enough to upgrade or work on it for long.  I know the problem is the AMD graphics card.  I have tried all kinds of things I have read about to get it to work correctly.  The open source driver for it does not work.  The proprietary driver does work, but then my Unity desktop disappears.  Is anybody aware of a fix for this where I can use the proprietary driver and still have my Unity desktop?

---

### Post by gordintoronto on 2013-06-23
If you leave the computer off overnight, then boot into Ubuntu, you should be able to use it for 20+ minutes unless the vents are plugged with dust.

See: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by treeclimber on 2013-06-24
Using it for 20 minutes at a time is not feasible.  It takes longer than that to download updates.  If you read what I wrote, it overheats with the open source driver, but I have no GUI with the proprietary driver.  Is there a fix for this?  I have researched this extensively, but, short of chancing bricking my computer, I have found nothing that works.  I know this is a problem for other makes of computer laptops, too.  Can anybody direct me to a solution that works?  I saw in Launchpad this has been a problem for over a year, at least.  I have use Ubuntu for years, and when I purchased a new laptop, I wanted to dual boot and us Ubuntu for most things.  But I can't due to the over-heating.  I don't want to ruin my computer!

---

### Post by terebet on 2013-06-26
> **treeclimber said:**
> I'm having problems running Ubuntu on my Dell 14z 5423  Ultrabook with an Intel i7 processor.  It has Windows 7 on it and a wubi install of Ubuntu 12.10.  It has an AMD Radeon HD 7570M Graphics card and IntelR HD Graphics 4000 integrated.  If I run Ubuntu, it overheats every time and I have to shut it off.  I can't run it long enough to upgrade or work on it for long.  I know the problem is the AMD graphics card.  I have tried all kinds of things I have read about to get it to work correctly.  The open source driver for it does not work.  The proprietary driver does work, but then my Unity desktop disappears.  Is anybody aware of a fix for this where I can use the proprietary driver and still have my Unity desktop?

I have the same laptop as you. You have two options
1 - Use opensource driver and disable the discrete graphic (see [http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/](http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/))
2 - Use the proprietary driver and follow this guide ( [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355))

Both solutions work for me.
Good luck.

---

### Post by treeclimber on 2013-06-27
Which do you suggest will work better?  Which is easier?  I have read numerous solutions, but most seem really complicated.  I haven't checked these out yer.  I will do that tonight.

---

### Post by sdm_cacto on 2013-07-05
Thanks terebet, you have solved a big issue for me, since solution no. 2 doesnt work in my laptop (amd 7570M) I've solved battery problems with solution no.1 .

> **treeclimber said:**
> Which do you suggest will work better?  Which is easier?  I have read numerous solutions, but most seem really complicated.  I haven't checked these out yer.  I will do that tonight.

treeclimber,  If you dont have a lot of time to deal with crashes, I suggest you solution no.1 since solution no.2 might let you without graphics (which isn't difficult to solve but only if you have the experience and time).

I have the same laptop as you but couldnt install the propiertary drivers. So i deactivated my external graphics until drivers are more mature (I still use the ext. graphics card in windows only to play games)

---

### Post by treeclimber on 2013-08-02
Neither solution worked for me because my computer overheats before I can get it done!  I guess I'm going to have to wait until Ubuntu fixes this problem.  I bought this Dell because that's what I have always had Ubuntu on before and had no problems.  Figures that now I can't use it.  I really am not happy with Windows!

---

### Post by sdm_cacto on 2013-08-05
If your computer overheats before you can get this done (you only need a terminal and takes a couple minutes ) you are probably having other overheating problems. For example, if you use a laptop, it's probably dirty and/or not refrigeration well

---

