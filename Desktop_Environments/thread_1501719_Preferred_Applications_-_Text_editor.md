---
title: "Preferred Applications - Text editor"
date: 2010-06-04
forum: Desktop Environments
---

### Post by sdaau on 2010-06-04
Hi all, 

I actually wanted to respond to this post: 

[Preferred Applications - Text editor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=7370")

however, as it is impossible since its read-only archive (btw, why lock old threads? Is it just because of saving computing resources - since sometimes a question could still be relevant even after some time)..

Well, anyway, there is a lot of frustration (at least from this user :) but also others) about [How to Change the Default Text Editor on Ubuntu With Nautilus]("http://tips.webdesign10.com/how-to-change-the-default-text-editor-on-ubuntu-with-nautilus"). 

A lot of searches will turn up with a suggestion for using [FONT=Fixedsys]update-alternatives[/FONT]; however, that one simply replaces the symlink for [FONT=Fixedsys]gnome-text-editor[/FONT], which in spite of its name, is **NOT** what is being used, say, when you right-click on a text file in Gnome. 

However, since time, after time, after time, I bump into this issue, here is how I managed to integrate gnome-text-editor approach with right-click in gnome (tried in 10.04) 

First of all, I'd use scite to replace gedit, so: ```
sudo apt-get install scite
```. 

Then, other docs on net would recommend running [FONT=Fixedsys]update-alternatives --config gnome-text-editor[/FONT]; but at this point, [FONT=Fixedsys]update-alternatives[/FONT] still doesn't know about scite, so we should do: ```
sudo update-alternatives --install /usr/bin/gnome-text-editor gnome-text-editor /usr/bin/scite 50
```Now we can run ```
sudo update-alternatives --config gnome-text-editor
``` and choose whatever number where scite appears. 

However, this now just changes the [FONT=Fixedsys]gnome-text-editor[/FONT] symlink - but that has yet nothing to do with right click. 

So, first of all, we should add a new desktop shortcut fro gnome-text-editor, since it doesn't as yet exist. The desktop shortcuts are situated in [FONT=Fixedsys]/usr/share/applications[/FONT] - and we can simply copy the existing entry for [FONT=Fixedsys]gedit[/FONT], and modify it so it refers to [FONT=Fixedsys]gnome-text-editor[/FONT]: ```
cd /usr/share/applications
sudo cp gedit.desktop gnome-text-editor.desktop
sudo nano gnome-text-editor.desktop
# ... and change all references to 'gedit', to 'gnome-text-editor' ...
# ... and finally save. 

```At this point, if you look at the Applications/Accessories menu, you will notice that there is a new item there, referring to gnome-text-editor, as a result of the previous operations. If you click on it, Scite should open. That's a good sign - one more step :) 

Finally, the MIME associations are kept in [FONT=Fixedsys]/etc/gnome/defaults.list[/FONT]; and if we open that file, we will notice that [FONT=Fixedsys]gedit.desktop[/FONT] is used in many other cases, that just the [FONT=Fixedsys]text/plain[/FONT] MIME type. So, to change this, we can simply do a search for **all** instances of  [FONT=Fixedsys]gedit.desktop[/FONT] in [FONT=Fixedsys]/etc/gnome/defaults.list[/FONT] in a text editor, and replace them with [FONT=Fixedsys]gnome-text-editor.desktop[/FONT]; we could use, say, nano: ```
sudo cp /etc/gnome/defaults.list /etc/gnome/defaults.list.orig # backup first
sudo nano /etc/gnome/defaults.list
# using alt+R, do a search for 'gedit.desktop',
# replace all with 'gnome-text-editor.desktop',
# save and close 
```Finally, all is ready - we just need to "refresh" the desktop with the new settings, which we can do with: ```
sudo service gdm restart
``` - and finally, when we right click on a generic text file, we should get "gnome-text-editor" (and therefore scite) as the first, default option to open the text file :) 

(*and this method seems also to have that benefit, that once the .desktop shortcut is in place, it should be possible to change the default text editor just by running [FONT=Fixedsys]update-alternatives --config ...[/FONT]*). 

Well, I'm glad I will not be looking for hours on the Net next time I have to do this :) (hopefully, if I didn't do a mistake above :P) 

Cheers!

---

### Post by &#1606;&#1575;&#1589;&#1585;&#1575;&#1604;&#1575;&#1588;&#1602;&#1605; on 2010-06-04
thanx

---

