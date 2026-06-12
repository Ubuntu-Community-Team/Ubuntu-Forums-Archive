---
title: "New to Ubuntu - Graphics Settings not saving after restart... slow desktop effects."
date: 2007-05-02
forum: Desktop Environments
---

### Post by Occam on 2007-05-02
First, let me list my system specs for you all:

Intel Conroe E6600 2.6GHz running at 2.81GHz
2GB RAM at Dual Channel
nVidia 8800GTX by XFX
Ubuntu Feisty Fawn 7.04

... that's all I can think of off the top of my head, but I believe that's what matters most.

So, I just installed Ubuntu about a week ago and was having issues installing my nVidia driver (along with a lot of other people), but after a lot of work, and a lot of help from my friend, I finally was able to get it fully working. So, here's what's left:

I use dual monitors. A 22" widescreen and a 17" regular, at 1650x1050 and 1280x1024 respectively. When I enable TwinView via the nVidia Control Panel in Applications > System Tools, it works fine, but I have 56 pixels of empty space not being seen by my 17" monitor because it's not tall enough, and this just happens to be big enough to not see the bottom toolbar. That's issue #1... not sure if there's a solution to that yet.

Issue #2: Whenever I restart the computer, Ubuntu boots back up into its regular 1024x768 on my 17" screen, while my 22" widescreen is disabled. None of my settings save, even after using the "Save to xorg" option in the control panel. I have tried every possible setup with TwinView, and tried to save the Xorg file at different points, but it just doesn't want to.

Lastly, issue 3: The desktop effects (i.e. the minimize effect, the close effect, etc. etc.) are sluggish and very clunky (? maybe not clunky, but its certainly not smooth). Given my graphics card, and the fact my friend's laptop runs it perfectly, I find this a little strange. We are both using Beryl, although it's worth mentioning this was happening before with me while using Compiz, which is why I wanted to try Beryl and see if it resolved the sluggish effects issue. Needless to say, it didn't. :( 

So this is my first post on the Ubuntu Forums. I hear the community here is fantastic. :) I hope you guys can help me out.


Occam

---

### Post by Sqwishy on 2007-05-08
> **Occam said:**
> Issue #2: Whenever I restart the computer, Ubuntu boots back up into its regular 1024x768 on my 17" screen, while my 22" widescreen is disabled. None of my settings save, even after using the "Save to xorg" option in the control panel. I have tried every possible setup with TwinView, and tried to save the Xorg file at different points, but it just doesn't want to. 
He he, sorry you had to wait 5 days for a reply, some community we are ^^
The problem your having (i think) is that the nvidia-settings can't write to xorg.conf because it isn't running under root. So i think this is how you do it, i'm at a windows box atm so i can't check if the command is right...
In the terminal:
```
sudo nvidia-settings
```
Then the term will ask you for your user's password so type it in. _Then_ saving to xorg.conf should work.
Otherwise, if that doesn't work, you will hafta edit it manualy. Just search these forums for a twinview howto or guide.
So tell us if it works?

Edit: Oh yeah, with your Issue #3, that's a problem with the 8800gtx drivers :( sorry doesn't seem to be a fix yet

---

### Post by tenmuses on 2007-09-13
I had the same issue and it was exactly as Sqwishy says; the xorg.conf file wasn't being rewriten.

when you attempt to save to xorg.conf from the nvidia config utility, click on the "preview" option that is available and then highlight the entire thing and copy it to the clipboard.

Open a terminal and use "sudo gedit" to open the text editor.  

navigate to /etc/X11/  and open xorg.conf.    Immediately after opening it, save it to a backup file (I used the filename xorg.conf.bak).

then clear the window, paste in the clipboard text (the new xorg.conf you captured from the nvidia-config preview window) and save that file as xorg.conf.   It will ask you if you want to replace the old one.  Click yes and reboot.

That did it for me.

---

