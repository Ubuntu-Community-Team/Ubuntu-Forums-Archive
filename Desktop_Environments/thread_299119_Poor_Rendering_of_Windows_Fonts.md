---
title: "Poor Rendering of Windows Fonts"
date: 2006-11-13
forum: Desktop Environments
---

### Post by aos101 on 2006-11-13
After a lot of messing around I still cannot get Windows fonts looking (what I consider) good on Kubuntu Dapper.  Overall the default fonts look OK in applications, but the Windows fonts (installed from the msttcorefonts package) on webpages don't look quite right in multiple browsers.  My main monitor is a LCD monitor connected using a DVI cable, so I need something to make fonts appear smoother otherwise they are really blocky (whereas you don't really need font smoothing with a LCD using an analogue connection).  

You can see some of the problems in the attached images.  In the first one the stem of the number two where it says "libcairo2-dev" almost looks like it has part of it missing, and I think the two lines coming off the upright part of the "k" on the last line look rather thin.  In the second image where it says "12 2005" again I think part of the two appears to be missing.  In the third image the capital bold "O" seems to be a bit furry at the top and bottom instead of being a sharp line.  I'm using the default font rendering with anti-aliasing on, and using sub-pixel hinting and a hint style of full.I've tried the autohinter but that makes some bold text of Windows fonts too bold.

I've tried the font patches [here](http://www.ubuntuforums.org/showthread.php?t=180647) which I think do improve things, but still have the same problems such as part of the number two missing.  If I enable the autohinter with these patches I think this gives the best font rendering and fixes the part of the "2" missing, but it brings other problems like some letters too close together and touching, or the vertical part of a capital "I" being to one side of the top and bottom parts.  

I do a lot of surfing and want to use the Windows fonts so I can view pages as the designer intended, but poor rendering of Windows fonts is a real show stopper for me using Kubuntu.  I did install SUSE 10.1 but that had the same problems with Windows fonts.  I want to use Kubuntu more, but having something so important not looking right is really annoying.  I am used to ClearType in Windows, but don't mind getting used to slightly different looking fonts if the letters are formed right (don't have bits missing etc).  

So how can I improve this?  Do other users see these same problems?  If so do you just put up with it?  Are other users with DVI connected LCD monitors happy with their font rendering of Windows fonts, and if so how did you get good font rendering of Windows fonts?  Thanks for any help on this issue.

---

### Post by trmiv on 2006-11-14
I'm having the same problem in ubuntu (edgy).  I also followed the instructions in the thread you posted (well the updated link for edgy at the top of the thread), and while the fonts look better, they need to improve.  The biggest problem I've had is exactly what you've mentioned, sometimes pieces of the fonts appear to be missing.  You can see in [this screenshot]("http://img85.imageshack.us/img85/4255/screenshottheinternetmosi8.png") of imdb's front page that the capital F's, P's D's, E's and B's are missing parts at the tops.  I've seen that in a lot of places and it drives me nuts.

---

### Post by aos101 on 2006-11-17
Its nice to know its not just me annoyed with this.  Really I'm amazed Ubuntu/Kubuntu is shipped with such obvious problems rendering what must be the most popular set of fonts in the world in terms of use.  Maybe I'll try upgrading FreeType to the latest version to see if that helps...

---

### Post by mercurysquad on 2006-11-17
System > Administration > Software Sources > Third Party > Add
**deb [http://www.elisanet.fi/mlind](http://www.elisanet.fi/mlind) ubuntu fonts**
Reload.

System > Administration > Update-Manager > Install all updates

Ctrl+Alt+Backspace

See if that helps...

---

### Post by aos101 on 2006-11-17
Are those packages for edgy?  I'm running Dapper, and they sound similar to the packages I've already tried (although perhaps they are different).

---

### Post by trmiv on 2006-11-17
> **mercurysquad said:**
> System > Administration > Software Sources > Third Party > Add
**deb [http://www.elisanet.fi/mlind](http://www.elisanet.fi/mlind) ubuntu fonts**
Reload.

System > Administration > Update-Manager > Install all updates

Ctrl+Alt+Backspace

See if that helps...

The picture I posted of imdb above is WITH those fonts.

---

### Post by aos101 on 2006-11-26
Does no one have a solution or experience these problems then?

---

### Post by PvSinNL on 2006-11-26
> **aos101 said:**
> Does no one have a solution or experience these problems then?
I'm afraid I don't have a solution, but Windows fonts are rendered in the same (or at least a very similar) manner on my laptop LCD.

This is xmag showing a part of your original message:

[IMG]http://xs309.xs.to/xs309/06470/xmag2.png[/IMG]

---

### Post by aos101 on 2006-11-26
Thanks for the screenshot PvSinNL.  When I zoom in and compare my screenshot of a "2" and yours I think they look the same, but maybe they are very slightly different.  

I'm sorry if my last post seemed a bit blunt, but this is just really bugging me.

---

### Post by konungursvia on 2007-03-11
Me too, I dislike windows, and love ubuntu, but my eyes are literally sore each day after working on ubuntu for about 2 months now. My eyes are used to crisper fonts, and they keep trying to "focus' the blocky and choppy and blurry font rendering in this os. It's the only real beef I have about linux. Once we fix this, we'll conquer the world.

---

### Post by John Bennett on 2007-03-25
> **konungursvia said:**
>  It's the only real beef I have about linux. Once we fix this, we'll conquer the world.

Same here.

Fonts in Windows are simply crisper and easier on the eyes.

I have struggled with this problem for years.  I have tried every distro and hack I could find.  

I remain hopeful.

---

