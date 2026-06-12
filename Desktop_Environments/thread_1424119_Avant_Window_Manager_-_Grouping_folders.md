---
title: "Avant Window Manager - Grouping folders"
date: 2010-03-07
forum: Desktop Environments
---

### Post by Kredible on 2010-03-07
Hello all, I have been tweaking my desktop adding a few useful applets and at the same time trying to keep it simple.
I came across this great tool, avant-window-manager that supports launchers and tasks. Now there is something I would really like to have, which is grouping up opened folders. I thought the Stacks applet would do it but I'm not getting there, the only way to group them is by dragging several folders inside the Stacks applet and then voilá;
I was looking for something more Windows like, where your Folders group up and clicking them expands all the opened folders.

Any tool out there?
Thanks in advance!

---

### Post by koleoptero on 2010-03-07
Go to the taskmanager tab in the AWN preferences dialog and add a launcher for nautilus by adding:

nautilus --no-desktop --browser .

in the command. Then select above the option "show dialog after long press". It should enable you to minimize/restore all file browser windows with a single click (and all other grouped windows for that matter).

I have a suspicion that this is not exactly what you're looking for, but I thought it might help.

---

### Post by armoftheland on 2010-03-08
I dont know if I understand completely, and as I don't think there is (that I know of) a solution for that in AWN yet, you could create a custom launcher to open a file created by you containing the files you want... Good Luck!

---

### Post by Kredible on 2010-03-08
Thank you for replying :)
Maybe I didn't explain myself that well, anyway, I am somewhat rookie in Ubuntu, therefor my skills are very limited.
Still I tried what you said koleoptero, but I wasn't lucky. I created the shortcut but I couldn't find the "Show dialog after long press" option, so it's all the same for now.

After some research online I have found that what I was looking for has something to do with Pin Tasks/Windows; Still I uploaded a screenshot of my Windows XP task bar configuration options! That's exactly what I am looking for, only for Ubuntu :p

See how the 2 Internet Explorer windows are grouped together? It would be great if there was some Applet out there to use with AWN that would work with the nautilus explorer.
I hope at least I managed to express myself better this time!

---

### Post by Ultra_Man on 2010-03-08
You're using the 0.39/0.4 version right? Well I'm pretty sure that it already does that. Just go to awn settings and go to task manager and make sure "group common windows" is checked.

---

### Post by Kredible on 2010-03-08
Hey there Ultra_Man, well as far as I know from the 'About' screen in AWN, it sais I am using 0.3.2.1.
According to [https://launchpad.net/awn/](https://launchpad.net/awn/) which I googled, it seems to be the latest version.

Now this thing came to my head a couple minutes ago, could it be related to Compiz settings or something? I am using 'Compiz 0.8.2'.

Am I missing some option there?

As to the awn settings menu the options related to task manager are regarding its appearence and not behavior.

Hm, I just googled for awn 4.0 and something showed up, could it really be that I am using an older version?:confused: I will check it out and update this thread then.
Thanks for notifying.

---

### Post by Kredible on 2010-03-09
Oh there you go...
It seems that there is another version, which is 0.3.9.
Just in case, the instructions I followed:

Added the PPA repository
```
sudo add-apt-repository ppa:awn-testing
```Updated previous version (and my distro aswell it seems...)
```
sudo apt-get update && sudo apt-get dist-upgrade
```Note: The following applies for 1st time installing AWN
```
sudo apt-get update && sudo apt-get install avant-window-navigator-trunk
```Now it's all set up and seems to be much more complete. The tasks grouping looks pretty great, now there is only one thing that's bothering me, the whole panel seems quite sluggish. Whenever I mouseover an icon it moves so slow! Regardless of the effect (Fade, Glow, etc).

Cheers to [Web Upd8]("http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html") for the post.

If anyone knows a workaround to this slow performance on awn, let me know please; otherwise it seems the 'stable' version is a bit more...stable :P

---

