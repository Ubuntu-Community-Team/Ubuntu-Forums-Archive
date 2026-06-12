---
title: "Shadows and Transparencies without Compiz/Beryl?"
date: 2007-04-25
forum: Desktop Environments
---

### Post by Emblem Parade on 2007-04-25
Yeah, yeah, I know everyone's raving about how Compiz/Beryl leapfrogged Vista and Mac OS. I admit I'm impressed. (Actually, I'm *not* impressed by Beryl's "configuration" panel, surely a euphemism for a UI design monstrosity.) Thing is, both are too buggy right now for everyday work. Crashes and glitches just make it impossible for me to keep them on constantly. As such, I entirely agree with the Ubuntu team's decision *not* to include them by default.

That said, I do want to enable some advanced desktop features, which shouldn't require 3D. On Windows XP, I was a happy WindowBlinds user, having a desktop with pretty shadows and transparencies. Both, I feel, are not merely eye candy, but real usability features, which help avoid clutter on the screen. With all the hype about eye candy on X, I admit I expected an equivalent to WindowBlinds to be ready for me by default on Ubuntu. Maybe I'm just especially stupid, but I can't find any way to enable those, and no Gnome theme seems to have them.

So, is there any way to do this on Gnome or Metacity? Or some other package? And if not, can someone provide some background on why this is so?

(I know that Metacity is supposed to have some of these advanced features, including 3D support. Is it still in the works?)

Thanks,
From an Otherwise Ecstatic Switcher
(should also be known as an OES... a well-known species in this forum...)

---

### Post by sethmahoney on 2007-04-25
There was something a while back (xcompmgr?) that gives you transparency (and maybe drop shadows?  I can't remember).  If I remember aright, it was really buggy though.  I'm surprised Compiz/Beryl is buggy for you - I've been using it for a few months with no major problems at all.  What's your hardware?  How did you install it?  Maybe there's some issue there that can be fixed?

---

### Post by RedSquirrel on 2007-04-25
Yeah, xcompmgr and transset are available in the repos (you'll need both for transparency). They are slow on my old box, but they might be better on a newer machine (?).

---

### Post by kpkeerthi on 2007-04-25
I've tried xcompmgr. It was buggy and unusable back then. Not sure now.

---

### Post by Emblem Parade on 2007-04-25
Thanks, folks! I looked around, and it seems that xcompmgr is getting pretty bad comments from people... I guess it's also not quite ready. Looks like Compiz/Beryl are the only way to go now. I'm surprised I need 3D support to allow for shadows and transparencies.

To Seth Mahoney -- I run Beryl/Compiz directly on Nvidia "restricted" drivers (no AIGLX or XGL). Actually, I just checked and Compiz doesn't seem to be working while Beryl is since my upgrade to Feisty. Go figure. Part of the bugginess may be that I'm running in a TwinView setup, using two monitors with different resolutions. Let me tell you, it was a huge pain in the *** to get to work, though it does work perfectly now.

But I feel Beryl is overkill... all I want is nice shadows around my windows! Does Metacity really not handle that? Is there a non-3D window manager that does?

---

### Post by Emblem Parade on 2007-04-26
OK, I decided to be helpful and try xcompmgr and transset out for myself and see. I have to say, I'm delighted at how simple they are conceptually -- almost no configuration, which is very Gnome-y and nice (unlike Beryl). There's a truly great howto here, which is very old, but works fine on Feisty:

[http://ubuntuforums.org/showthread.php?t=75527](http://ubuntuforums.org/showthread.php?t=75527)

I'm still worried by the many bugs mentioned, but it seems especially easy to turn on and off. And, the fact that it's not included in Ubuntu upon installation says a lot. Anyway, I'll give it a whirl for a while and report back here as to how stable it is of Feisty... stay tuned...

---

### Post by Emblem Parade on 2007-04-27
Oh dear. Less than a day into my "experiment," and I can unequivocally say that xcompmgr is *even worse* under Feisty!

After a few hours, I couldn't run programs. I'm not sure what the problem was, but they didn't start. Currently running programs failed very bizarrely.

Then, X crashed.

On the terminal, I started seeing insane kernel alerts having to do with ext3 errors.

I panicked, of course, rebooted, and now everything is back to normal. Needless to say, I won't be running xcompmgr again!

So, it looks like there's no simple or bug-free compositing available for Ubuntu. All we have are Compiz and Beryl, both unstable and heavy.

---

### Post by tristan on 2007-04-27
> **Emblem Parade said:**
> Thanks, folks! I looked around, and it seems that xcompmgr is getting pretty bad comments from people... I guess it's also not quite ready. Looks like Compiz/Beryl are the only way to go now. I'm surprised I need 3D support to allow for shadows and transparencies.

To Seth Mahoney -- I run Beryl/Compiz directly on Nvidia "restricted" drivers (no AIGLX or XGL). Actually, I just checked and Compiz doesn't seem to be working while Beryl is since my upgrade to Feisty. Go figure. Part of the bugginess may be that I'm running in a TwinView setup, using two monitors with different resolutions. Let me tell you, it was a huge pain in the *** to get to work, though it does work perfectly now.

But I feel Beryl is overkill... all I want is nice shadows around my windows! Does Metacity really not handle that? Is there a non-3D window manager that does?

Maybe this won't really help you, but have a look at Xfce 4.4 (or 4.39 in Dapper). If you have composite enabled in your xorg.conf then you can quickly enable soft shadows and transparency in the "Window Manager Tweaks" section of the Xfce settings . With a little bit of tweaking I got my Xfce desktop to look almost exactly the same as the ubuntu gnome desktop, but with nice shadows and transparency (not to mention a little faster).

---

### Post by Emblem Parade on 2007-04-27
Thanks, Tristan, it actually does help.

I have another machine with Xubuntu, and I'm really impressed by how much Xfce accomplishes with so little. I'd even say that the upgrade to Feisty seemed more of a jump on Xubuntu than on Ubuntu, for my uses. And, when it comes down to it, I can't actually list many significant advantages Gnome has over Xfce. And, as you point it, it's actually more advanced in some ways.

It's not exactly on topic, but because a switch to Xfce is a viable option for people who want a prettier desktop, can you perhaps mention a few features that I or anybody else doing the switch would lose?

---

### Post by tristan on 2007-04-27
> **Emblem Parade said:**
> Thanks, Tristan, it actually does help.

I have another machine with Xubuntu, and I'm really impressed by how much Xfce accomplishes with so little. I'd even say that the upgrade to Feisty seemed more of a jump on Xubuntu than on Ubuntu, for my uses. And, when it comes down to it, I can't actually list many significant advantages Gnome has over Xfce. And, as you point it, it's actually more advanced in some ways.

It's not exactly on topic, but because a switch to Xfce is a viable option for people who want a prettier desktop, can you perhaps mention a few features that I or anybody else doing the switch would lose?

Glad to help EP. I actually find that I don't seem to miss much between Xfce / Gnome. They both use GTK so look very similar, and can be themed to look identical. I think the drag and drop is more advanced in Gnome, so it's easier to drag icons from menus to taskbars for instance. 

The bottom line is: if you like the features of both, use both! I do.

---

### Post by Emblem Parade on 2007-05-07
Well, the saga has ended. I chickened out of moving to Xfce, just because I have a lot invested in my desktop already, and didn't want to risk too much work. But people should be aware that switching to Xfce or even KDE is a decent option for basic shadows and transparency.

My solution, staying with GNOME, was to use the version of Compiz included in Feisty, but instead of using the "desktop effects" manager, I used the more detailed gnome-compiz-preferences. There, I could enable just the bare minimum and remove the wobbly windows, cube, and other effects I find distracting. So, I get shadows, transparency, and the added speed of compositing, exactly what I wanted! And, as far as I can see, it seems stable.

It seems to me that a lot of the Compiz bugs have to do with wobbly windows. So, just disable it!

---

### Post by Nythain on 2007-05-07
kde with the right windeco/style and the optional xcompmgr has some groovey customiability

---

### Post by Emblem Parade on 2007-05-08
OK, latest update in my adventure, using Compiz with disabled wobbly windows.

First, people should be aware of [this bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/95011"). You're going to have very buggy behavior with minimize/maximize. I utterly understand why this isn't enabled by default on Feisty!

Also, I've been having trouble with screensavers, and so have many other people. For some, screensavers don't start. For me, I have trouble getting back from screensavers sometimes. Sometimes it takes a long time. Other times, I need to restart X. I've also had to reboot once or twice. Sucks. Disabling them was the perfect workaround. Who needs screensavers anyway? My screen is already saved. Hallelujah!

Generally, I'm a bit annoyed by how Compiz moves around windows on TwinView. Why can't it just imitate Metacity's behavior? Darn, I just really like Metactiy, boring and perfect for me. I just hope Metacity's compositing features make it into the repositories soon.

---

### Post by FuturePilot on 2007-05-08
If you're up to it the XFCE desktop has a built in compositor which will give you some basic but nice looking compositing. There really is no need for something like Window Blinds because you can already theme anything the way you want it.

---

### Post by zero-9376 on 2007-05-26
Does anyone know if window decoration transparency is possible without compiz/beryl/xcompmgr. Im looking for simple see the desktop fake transparency for my laptop which uses and S3 chipset card. I know KDE has kwin themes with this sort of transparency (crystal theme i think) so what about gnome, the panel and the terminal can do it what about window decorations?

Thanks

---

### Post by RedSquirrel on 2007-05-26
> **zero-9376 said:**
> Does anyone know if window decoration transparency is possible without compiz/beryl/xcompmgr. Im looking for simple see the desktop fake transparency for my laptop which uses and S3 chipset card. I know KDE has kwin themes with this sort of transparency (crystal theme i think) so what about gnome, the panel and the terminal can do it what about window decorations?

Thanks

Fluxbox window manager has transparency for window decorations and you can set the transparency level from 0 (clear) to 255 (solid). However, it will only pick up transparency from your desktop wallpaper, not from applications beneath the top window. You would need something more advanced (e.g., xcompmgr) for that.

---

### Post by zero-9376 on 2007-05-28
the pc im using is also used by others so fluxbox might be a bit much to ask of them, can it be used to draw the window decorations only?

---

### Post by RedSquirrel on 2007-05-28
> **zero-9376 said:**
> the pc im using is also used by others so fluxbox might be a bit much to ask of them, can it be used to draw the window decorations only?

Yes, in theory Fluxbox can replace Metacity as the window manager that GNOME uses. I don't know how well it works for that purpose because I don't use GNOME, so it's up to you to give it a try if you want to. [Here]("http://fluxbox-wiki.org/index.php/Faqs#Can_I_use_fluxbox_as_the_window_manager_in_GNOME") are some instructions. Perhaps someone else who has tried this can tell us how well it works when Fluxbox is used as the window manager for GNOME...

---

### Post by mannheim on 2007-05-28
You can also use gnome and replace the metacity window manager with kwin. You can then enable transparancy and shadows in kwin. This is what I used to do before switching to compiz. I really liked kwin -- it worked fine under gnome, and has a lot of configurable features that I found genuinely useful. You don't have to install all of kde to use kwin, though it does pull in a lot of dependencies.

---

### Post by AnRa on 2007-05-28
You should try to [replace metacity by xfwm4](http://ubuntuforums.org/showthread.php?t=88393) ;)

---

### Post by zero-9376 on 2007-05-29
I have just tried out the xfwm4 and it looks good but do i need to enable compositor to only have window decoration transparency?

---

