---
title: "Files only want to open in gedit"
date: 2009-12-27
forum: Desktop Environments
---

### Post by CAurora on 2009-12-27
I have a weird problem with my preferred applications on my 9.10 installation (standard GNOME): for some reason at one point during the last few days, shortly after I installed it completely new, I lost the preferred applications to .pdf, .mp3, . ogg, jpg., actually, now that I look at it, basically everything except for .txt and .odt. 
Instead of the intended application now **gedit** wants to open the file, and there is no way for me to change this again. I can open my files by "open with..."->"open with another program", but I can't set this program as permanent, but have to manually choose the application to use every time instead.
does anybody here have any idea what could have cause that? and how I can get rid of it?

---

### Post by kiridude on 2009-12-27
Right click the file > properties > open with

That will set the default for all files of that format.

---

### Post by CAurora on 2009-12-27
Uhm... yeah... basically that is the problem. 
It doesn't work. 
As I wrote before, the only thing appearing are the "open with gedit" and the "open with..." option. 
The latter gives me the option to open it with gedit, mousepad, openoffice or abiword, or to "Open with another program".
This last option gives me in one tab an empty list of recommended applications and a field I can put in a normal command, in the other tab it gives me a list of the applications I can choose from (with all the applications I would need). 
Unfortunately it does not seem to remember the application I chose last time, so I basically have to repeat this process (right click, open with..., open with another program, then either put in the right command or choose from the list) every time I want to open anything which is not .odt or .txt.

I was hoping there might be some option somewhere to set those things, but so far I haven't found more than the "preferred applications" dialogue in Administration which lets me set my Browser, etc. Isn't there any comprehensive option where I can set what file to open with what program? Or even better, just switch the whole system back to how it was when I installed it 5 days ago?

---

### Post by CAurora on 2009-12-27
ah... and yes... there is no file > properties > open with-dialogue anymore. it disappeared the same time the files started to only accept gedit as their application...
file > properties only yields 2 riders: general and permissions

---

### Post by hariks0 on 2009-12-28
Why don't you try ubuntu tweak to do this?

---

### Post by CAurora on 2009-12-28
I installed Ubuntu Tweak. According to what it tells me my files all have the proper links. So mp3 should be opened by vlc, zip should be opened by Archive Manager and so on... only they aren't. Even changing those settings doesn't help. 
I now noticed that some files do not have gedit as their allocated application at all, but instead show the empty "open with another program" list from the beginning.

---

### Post by kiridude on 2009-12-28
Your original post talked about right click > open with. that is why I suggested right click > properties to make it permanent. I see that also doesn't work.

Since nobody seems to have an answer for you, I would suggest re-installing since its a new installation anyway.

---

### Post by doas777 on 2009-12-28
before you rebuild. check this out:
[http://ubuntuforums.org/showthread.php?t=1151325](http://ubuntuforums.org/showthread.php?t=1151325)

---

