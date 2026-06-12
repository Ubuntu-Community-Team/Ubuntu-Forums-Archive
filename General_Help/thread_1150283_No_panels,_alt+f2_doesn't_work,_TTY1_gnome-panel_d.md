---
title: "No panels, alt+f2 doesn't work, TTY1 gnome-panel doesn't work"
date: 2009-05-05
forum: General Help
---

### Post by oOarthurOo on 2009-05-05
I am running Ubuntu Jaunty. Twice now I have restarted Ubuntu after making no changes, and applying no updates, and the following strange problem occurs:

Ubuntu boots normally, gdm logs in normally, login sounds play, desktop wallpaper shows up, but I am not left with a usable desktop. No panels. Alt+F2 doesn't work. Right-clicking doesn't work. All I can do is control+ alt+delete to reboot. 

I switched to TTY1 and attempted to run gnome-panel, but it couldn't open the display. Attemping to switch back to TTY7 resulted in an unusable display.

The first time this occurred I simply reinstalled everything. The second time I kept the home directory. Upon rebooting the second time (after a clean install) the problem persisted, meaning there is something wrong with the gnome-config in my users home dir. I deleted folders like 'gnome' and 'config' and anything else that I felt wouldn't cause data loss. The result was a perfectly working desktop.

So, in summary, I think I've come across a bug whereby the laptop will suddenly and without provocation refuse to startup normally. Separate bugs are preventing me from using viable workaround suggested elsewhere on the forums for similar problems. What I really need is to understand what is going wrong.

Most posts on the subject are related to people using the normal desktop along with the netbook desktop, however I am only using standard ubuntu jaunty.

At this point I am going to create a separate user, leaving things at a default setting so that I can at least log in and troubleshoot my users config files if something should go wrong again, though, I'm a big baseball fan and I think 3 strikes you're out. Unless I can find the excuse - the thing that is causing this seemingly random failure.

Thoughts and possible workarounds, links to relevant bugs, etc., are greatly appreciated.

AM

---

### Post by oOarthurOo on 2009-05-19
An update on the problem: so far so good. I've made about 95% of the same customizations without trouble. A couple of differences to note, however, the first being that I have not touched the gdm-login, I have left it at the default for Jaunty. Before I was using the new-wave face browser:

[http://gnome-look.org/content/show.php/New+Wave+Gdm+Face+Browser?content=88403](http://gnome-look.org/content/show.php/New+Wave+Gdm+Face+Browser?content=88403)

The only troubling issue is that I have suddenly encountered the inability to open folders. Trying to open any folder via places or clicking on the home icon results in a message saying, sorry, no application exists to do that. I restored nautilus as the app responsible for opening folders, but I seem to recall this happening before I started to run into problems last time as well.

---

### Post by oOarthurOo on 2009-05-19
Jackpot. The problem reoccured. I've narrowed the issue down somewhat, and have found that deleting entries using alacarte causes the behaviour to reoccur. A workaround, for the moment, is to delete the users .local directory, then restart. 

I will experiment some more to see what sort of customizations are likely to trigger this bug. At the moment, I have filed a bug report against alacarte here: [https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/378422](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/378422)

---

