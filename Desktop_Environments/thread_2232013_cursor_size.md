---
title: "cursor size"
date: 2014-06-29
forum: Desktop Environments
---

### Post by cmcanulty on 2014-06-29
I have read to paste this into 3 different locations which is correct? .Xdefaults, .Xdefault, or .Xresources ? I am running xubuntu 14.04 64 bit thank you
```
Xcursor.size: 48
```

---

### Post by Dennis N on 2014-06-29
Only **.Xdefaults** exists on my Xubuntu 14.04. I would put the setting in there after any other content. If that fails, it would make sense to create the other two files and try those. That said, I think the cursor theme has to support multiple sizes before this size command will work.

Did the cursor size chooser in **Settings > Mouse and Touchpad >  Theme** have any effect?

---

### Post by cmcanulty on 2014-06-29
only in firefox the rest is tiny and white. This same behavior on 10 machines I run

---

### Post by Dennis N on 2014-06-29
> **cmcanulty said:**
> only in firefox the rest is tiny and white. This same behavior on 10 machines I run
I used DMZ-black as a test, used the size chooser in Settings, and it changed size in some places (Firefox and Libre Office Writer in particular) as you describe. The extra settings you give didn't have any effect for me beyond what the size chooser did. Did they work for you?

I found that if you are willing to keep the default size, changing the system default cursor with update-alternatives to another choice makes that new cursor active everywhere (after installing it first if it's a new cursor you downloaded from some source). In Xubuntu, I didn't even have to select it as the cursor to use in the Settings dialog - that is just left as default. Maybe you know this already.

So, if you want an uniform larger cursor for the Library patrons, one way is to find and use one that is larger in size by default so you can just use the default size. That is what I have been doing. The one I have been using for a long time is called Flatbed Cursors - comes in colors black, blue, green, orange and white and sizes small, regular, large, and huge. 

The source is:

[http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027](http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027)

If you find a way to make DMZ and the other resizable cursors uniform in size everywhere in Xubuntu, I would like to learn how so I can add another tool to my toolkit. In the meantime, I use and am happy with Flatbed Cursors. And there are certainly other cursor styles at the same source that are large if you look for them.

---

### Post by ibjsb4 on 2014-06-29
Cursors larger by default

crystalcursors
and
big-cursor

use
sudo apt-get install ..

---

### Post by cmcanulty on 2014-06-30
thanks all it seems weird that the settings manager lets you set the color and size but it only works in firefox . I don't code but it seems like it wouldn't be hard to fix this bug. I need a large cursor due to poor eyesight

---

### Post by Dennis N on 2015-05-19
Adding this update for any interested users:

I have found that the newest Xubuntu 15.04 now handles resizable cursors correctly. Below is a screenshot of the cursor over the forum editor window with redglass at maximum size. The setting is easy in the Mouse and Touchpad settings under the Theme tab.

[ATTACH=CONFIG]262077[/ATTACH]

Tested this giant red cursor for a while, with no reversions to a smaller size, and no switches to a different cursor theme.

---

### Post by cmcanulty on 2015-05-19
wow that would be a treat I still have 2 library computers that won't do anything but tiny white even with all the tweaks. I wonder if there is a way to get that functionality into 14.04 without going to 15.04 as I like to stick with LTS

---

### Post by Dennis N on 2015-05-19
> **cmcanulty said:**
> wow that would be a treat I still have 2 library computers that won't do anything but tiny white even with all the tweaks. I wonder if there is a way to get that functionality into 14.04 without going to 15.04 as I like to stick with LTS

I wondered that too. One of my computers has Xubuntu 14.04.1 LTS which I upgraded to XFCE 4.12 in April. I thought the fix might be in that newer Xfce version, but testing found it still has the same cursor problems. So it's some other change in 15.04 that fixed it. Anyway, I'm very happy to have discovered this. Using bigger redglass right now.

---

### Post by Dennis N on 2015-05-21
> **Dennis N said:**
> Adding this update for any interested users:
I have found that the newest Xubuntu 15.04 now handles resizable cursors correctly. 

Well, I spoke too soon on this one. It is not all we had hoped for. The larger size the cursor is not being saved on shutdown. However, the new size IS persistent during the session when set. That alone is an improvement over previous behavior. Now I am wondering if it could be set to the desired size with a autostart script on log in. This is something that should be investigated.

[COLOR="#000080"]EDIT: See post #17 for the complete solution found for Xubuntu 15.04[/COLOR]

---

### Post by cmcanulty on 2015-05-21
I spent all afternoon trying to get this working on 2 library computers with no luck and just got everything all screwed up. this issue is really irritating and has been going on for years.What really kills me is the 2 laptops have the DMZ large black cursor 48 pt in all apps for the limited user, but the admin account has a tiny black or white cursor, I have tweaked all the suggestions downloaded themes ad naseum and can't figure this out. I have added files to icons, etc/applications xdefault xresources and used galternatives how can such a small glitch be so hard to fix.We need a detailed report on how to find cursors, how to install themes, etc and something that works in all apps and all users!

---

### Post by Dennis N on 2015-05-21
I wish I had an answer for your two balky computers. I don't.

But, it is better now than before on mine. At least now it stays without change for the remainder of the session after being resized in the Mouse and Touchpad dialog in Xubuntu 15.04. Before this, the resized cursor was very erratic as to size as discussed earlier in this thread.

I've also been trying out Ubuntu MATE 15.04. It also has a dialog to resize the cursor - it's the same dialog that existed in the Gnome 2 desktop (as used in Ubuntu 8.04 and 10.04). I've found that in Ubuntu MATE resizing does survive restarts (2 so far) and the cursor retains the larger size. Changing the OS or even the desktop environment is probably not a solution for your computers, but FYI it is working in MATE. If you ever add some computers, it might be something to consider on a new install.

[COLOR="#000080"]EDIT: See Post #17 for the complete solution found for Xubuntu 15.04[/COLOR]

---

### Post by Elfy on 2015-05-22
Hi.

So has anyone reported this as a bug? 

I've checked 14.04 - think I see similar, though I've had cursor new size retained on reboot.

14.10 - see size retained on reboot in vm

15.04 - see size retained on reboot - though mouse size appears to change.

15.10 - see size retained on reboot - seems fine everywhere.

Is this what you see? (This is a 14.04 Xubuntu as downloaded. Note: added the xfce4.12 ppa,that made no difference)

[View My Video](http://tinypic.com/r/2ag8fhj/8)

This is what I see with 15.10 

[View My Video](http://tinypic.com/r/34fhe2w/8)

---

### Post by cmcanulty on 2015-05-22
this has been a bug for years and seems to crop up on any debian based linux or at least all the buntus

---

### Post by Elfy on 2015-05-22
> **cmcanulty said:**
> this has been a bug for years and seems to crop up on any debian based linux or at least all the buntus

ok - point me at an xfce one please.

---

### Post by cmcanulty on 2015-05-22
xfce is the same as the other buntus I can't believe no one can fix this after years of it

---

### Post by Dennis N on 2015-05-22
OK, I have it now. This procedure seems to make the resized cursor persistent across sessions in Xubuntu 15.04. 

_Proposed Solution_
Suppose I want redglass in size 32:

1) choose redglass, size 32 in Mouse and Touchpad dialog.
2) set redglass as the default with update-alternatives
3) create the file ~/.Xresources  (it did not exist on my systems) with the single line:

[FONT=Courier New]Xcursor.size: 32[/FONT]

With all three steps, on reboot the cursor is the small redglass on login screen, BUT now resizes automatically to 32 upon log in, and doesn't vary. 

Missing either (2) or (3) it remains small after login and has to manually be reset.

--------------------
Testing done: changes persist over 2 restarts on computer #1; also done on a second computer and tested successfully with one restart. Both OS were Xubuntu 15.04. We'll see if continued use reveals any problems, but I think it's fixed. 

My hunch is that this solution won't work on Xubuntu 14.04 after seeing the erratic behavior within a session (as in earlier posts on this thread). But check it out.

[COLOR="#000080"]EDIT: Long-term testing shows the solution here solves the problem of using resizable cursors in Xubuntu. However, it only works for Xubuntu 15.04 (most recent version available).[/COLOR]

---

### Post by cmcanulty on 2015-05-22
2 totally weird behaviors I am experiencing: galternatives won't allow me to pick any other option, in other words the radio buttons don't work. On another laptop galternatives when I pick x cursor theme it goes to xvnc and will never go to xcursor. The weirdest though is on 2 laptops I have the large black cursor 48pt on the limited user account but can't get anything except ultra small white cursor on the admin account. How is that even possible? I have done the xdefaults, xresources etc

---

### Post by Dennis N on 2015-05-23
> **cmcanulty said:**
> 2 totally weird behaviors I am experiencing: galternatives won't allow me to pick any other option, in other words the radio buttons don't work. 

Hi cmcanulty,

Alternatives Configurator (galternatives) is broken in 14.04 releases. 

[https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709](https://bugs.launchpad.net/ubuntu/+source/galternatives/+bug/1309709)

I did the following to get it working:

```
dmn@Roxanne:~$ cd /usr/sbin
dmn@Roxanne:/usr/sbin$ sudo ln -s /usr/bin/update-alternatives update-alternatives

```

---

### Post by cmcanulty on 2015-05-23
that command gives me an error

```
cmcanulty@ubuntu1:~$ cd /usr/sbin
cmcanulty@ubuntu1:/usr/sbin$ sudo ln -s /usr/bin/update-alternatives update-alternatives
[sudo] password for cmcanulty: 
ln: failed to create symbolic link &#8216;update-alternatives&#8217;: File exists
cmcanulty@ubuntu1:/usr/sbin$ 

```

---

### Post by Dennis N on 2015-05-23
That workaround came from the bug report. Essentially, the problem was that galternatives uses update-alternatives behind the GUI to do its work, and it was hard coded to use /usr/sbin/update-alternatives (i.e. not rely on the OS lookup of the command). It failed to work because update-alternatives was in /usr/bin. So to fix that a link is made from /usr/sbin to /usr/bin. That was the case in my 14.04, There was nothing named update-alternatives in /usr/sbin, and  my link was created. I remember checking these directories before I tried the solution myself.

So, it seems you already have a file (probably the symbolic link) in /usr/sbin named update-alternatives (which is the reason the OS will not create it). If so, you already have this fix in place. Could you have a later point release in which this may have been fixed? My 14.04 that was fixed is the original release.

Here is the symbolic link in question in Xubuntu **15**.04. In 15.04, It was included as part of the installation.

```
dmn@Daphne:~$ ls -l /usr/sbin/update-alternatives
lrwxrwxrwx 1 root root 26 Apr 10 21:30 /usr/sbin/update-alternatives -> ../bin/update-alternatives

```

See what you get from ```
ls -l /usr/sbin/update-alternatives
``` It will show the same as my output if the link exists. 

I have another install of Xubuntu 14.04 where this fix was never done. I can check that and see the state of these directories. I also have the Ubuntu MATE 14.04.2 point release I can check.

---

### Post by Dennis N on 2015-05-23
/usr/sbin/update-alternatives doesn't exist in my unfixed Xubuntu 14.04:

```
dmn@Daphne:/media/dmn/Xubuntu-1404$ ls usr/sbin/update-alternatives
ls: cannot access usr/sbin/update-alternatives: No such file or directory

```
Also doesn't exist in latest point release of Ubuntu MATE 14.04.2 (also unfixed):

```
dmn@Daphne:/media/dmn/U-Mate-1404.2$ ls -l usr/sbin/update-alternatives
ls: cannot access usr/sbin/update-alternatives: No such file or directory

```

While the actual file exists in /usr/bin:

```
dmn@Daphne:/media/dmn/U-Mate-1404.2$ ls -l usr/bin/update-alternatives
-rwxr-xr-x 1 root root 43544 Apr  9 08:51 usr/bin/update-alternatives

```

Very curious. No link in /usr/sbin in this point release. I will be interested to see what you have as **/usr/sbin/update-alternatives**.

Best regards

---

### Post by cmcanulty on 2015-05-23
I have to wait until Thursday at the lib to check that. My home machine is running 14.04.2 xubuntu and the link is there on my laptop, the other 2 problem laptops are at library, thanks

---

### Post by cmcanulty on 2015-05-24
just for the heck of it I installed 15.04 on virtual box and the mouse behavior is still a mess. In settings manager I pick black 48pt and it stays small and white, even after a reboot seems like this will never be fixed

---

### Post by Toz on 2015-05-24
What's interesting for me, is that I'm experiencing the exact opposite. Cursor issues have been fixed for me in Xubuntu 15.04. All I need to do is the make the change in the Mouse and Touchpad applet in Settings Manager and it works. It also survives a reboot.

I also just did a fresh install if Xubuntu 15.04 into Virtualbox and the same happens. All works as it should now. 

I'm not sure why its not working in your VB.

---

### Post by cmcanulty on 2015-05-24
Here is some more weirdness, after a virtual box poweroff rather than a restart. On the mouse and touchpad theme tab all except handhelds will increase the size now and change color but it doesn't survive a reboot. Isn't there a coder that could explain where these settings are and how to fix this?

---

### Post by cmcanulty on 2015-05-28
Is there really no way to get a black 48 pt mouse in xubuntu 14.04? I have googled and tried fixes for days and nothing works. Can only get large mouse in firefox. I have done theme installs, dconfig settings , alternatives fixes and everything else I could find searching back in forums for at least 3 years. I can't believe this is unfixable.

---

