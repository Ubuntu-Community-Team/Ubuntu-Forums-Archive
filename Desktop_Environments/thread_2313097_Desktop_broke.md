---
title: "Desktop broke"
date: 2016-02-09
forum: Desktop Environments
---

### Post by de Bacon on 2016-02-09
I am running xubuntu 14.04 on a different partition and HDD multi boot (grub) with several flavors of ubuntu.  I use xubuntu as my default OS.  Last night looking at Youtube video, actually downloading some, I noticed some odd behavior, in Firefox, I tried to close it, but it didn't close.  I forced it closed, (Alt+F4) popup screen showed up with options to wait or close.  I chose close it, or exit (what ever that pop-up box states I don't recall).  It was late, I then shut down the computer normally no problems.

This morning I booted the system, logged into the xubuntu OS but there are problems.  All that shows up is the desktop wallpaper, no icons, no menus, nothing other than the wallpaper.  I am flummoxed.

I did use a boot disc, opened gparted and ran a check of the OS's partition.  In the past that has restored problems but nothing came of that with this instance.  I really don't know what to do at this point.  

I imagine something can restore the system but???  I don't know.

Any assistance will be greatly appreciated,

I have been fooling around trying to figure how to correct this issue but I don't have a skill set that allows me to do very much with the command line.  I can get to the prompt after logging in by (Ctrl+Alt+F1) yet it does me no service without knowledge as to commands.   I have tried using the grub menu, (advanced) but that seems to not actually work, I may be wrong, yet if I select the "fix broken packages," I see the prompt, click "Yes" it seems to go to a shell like situation, with the previously mentioned prompt still in the upper portion of the screen, leaving a prompt like space below, that has some statements (I don't know what they are or what they mean) leaving a seemingly functionless situation.  That is I can type stuff in but typing commands there does nothing at all.  

Another thing I recall with my really poor memory,  when I did initiate the shell (Ctrl+Alt+F1) there was a message that there are 10 packages that can be updated.  I don't know how to do that though.  I attempted to open synaptic (sudo synaptic) but from the shell the GUI won't open and there is a message stating that it can't open, for reason (don't recall words)  

Oh I also was able to see the home directory which looks to be complete, though it didn't show any of the hidden files.  I could only see files and folders that I have made.

I shall keep on trying.
Thanks for reading.  Mayby someone understands this situation and provide an assist.

---

### Post by Habitual on 2016-02-09
Ctrl+Alt+F1
login as yourself.
```
mv ~/.config ~/.config.backup
mv ~/.gconf ~/.gconf.backup
exit
```
Ctrl+Alt+F7
login.

---

### Post by grahammechanical on 2016-02-09
> when I did initiate the shell (Ctrl+Alt+F1) there was a message that there are 10 packages that can be updated.

To get that message you would have had to enter your user name & password and the run the command

```
sudo apt-get update
```

You are doing things but in telling us you are not clear about what you are doing and giving next to no information about the results. It is impossible to help you. I am no even sure what the problem is. Odd behaviour in Firefox? What does "odd behaviour" mean? Xubuntu loading to a desktop but with only the wallpaper and no menus?

If the advice given by habitual does not work, then please start again from the beginning and fix on the one problem of getting to a working desktop.

Regards.

---

### Post by de Bacon on 2016-02-09
I said it quite clearly.  When I booted up this morning to xubuntu, upon login, I had a screen with wallpaper, there was nothing else, zip, nil, a blank screen of wallpaper without any way to interact with it.  At least I thought what I stated above was clear.  I guess I could have said the gui was gone, but didn't think of using that terminology.  I also did say I was viewing Youtube video and downloading it, when I noticed odd behavior and how I had to shut it down.  That is all I know.  I shut it down figuring all to be well in the world of the computer, but I woke today to find my computer was not so well.  

Anyhow, 
I did what Habitual wrote and it sort of worked.  I lost all of my customized panels but and desktop settings, but that is fixable with a bit of tedium.  It is also better than other possibilities.  

Habitual: 
Thank you very much for the assist.  It got me from no-place to someplace else.  Soon enough I believe all will be as it was, I think.  I think and therefore I am.

---

### Post by Habitual on 2016-02-10
Glad it worked out.

---

### Post by de Bacon on 2016-02-10
Habitual, 
and others,

Thanks for the assistance yesterday.  Long term though, it didn't work.  There is something really odd going on in that OS.  This morning I tried to open a .odt LibreOffice document to find LibreOffice wouldn't open.  Thus, I went into Synaptic and re-installed all of LibreOffice.  The LibreOffice still didn't open,  It showed a little popup box that stated some nonsense to me, and being in a hurry with need to access the document, I rebooted to a different OS, KXStudio 14.04.x (where I am working now) to access the document.  That was not an issue from the KXStudio OS.  I then went about my task.  Upon completion of the pressing matter, I rebooted and went back to Xubuntu 14.04.  Again back to no GUI, just a screen of wallpaper, nothing more.  I went through the procedure I did yesterday, running the commands you posted above, but there was no change this time.  

Now I am thinking that it might be something to do with encryption as the partition that Xubuntu 14.04 is on, is encrypted.  (This is the first time I used encryption for anything. Yes I have the key, but don't really know how to see or know if that is an issue)   I personally have no knowledge of encryption other than it is, thus no way to really know anything else about it.  But I have no real understanding of the trigger which caused this situation in the first place.  

What I think I want to do from here is to access the data through the shell (Ctrl+Alt+F1) from the no gui log-in, and retrieve some of the data, email mostly but a couple other files then start over with a fresh install on that partition.  The situation seems bleak to me.  I really don't know that I'd be able to read any of the retrieved data if I can actually move it to a different location on a different partition.  That is what I mean about not knowing about encryption.  I simply don't know what it actually does, how it does what it does or where it does it.  I seem to think it is sort of like a doorway that has a lock on it, that prevents access from outside places but I am unsure if my assumption is correct.  

This is where I am at right now, back to phase zero, wondering.  The good thing is that very little is on the partition in question.  

Thanks again, and thanks for reading to those who have.

---

### Post by de Bacon on 2016-02-12
This topic is and shall remain unresolved.  I made it go away through a fresh install with a similar flavor of Ubuntu, by returning to UbuntuStudio.  It is also xfce based.   Again thanks to those who helped and those who read the thread.  I don't know what happened nor why.

---

