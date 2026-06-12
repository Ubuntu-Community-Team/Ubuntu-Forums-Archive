---
title: "Call nemo from activities menu"
date: 2022-04-04
forum: Desktop Environments
---

### Post by drechsel on 2022-04-04
I'm using nemo instead of nautilus. I executed all the steps recommended in various articles, so most things work nice with nemo, including nextcloud integration.

One thing bothers me and I cannot find a solution:
When I search for a file with the "activities" feature, nautilus is used, when I choose one of the files found in the activities window, nautilus will launch. When I uninstall nautilus, no files are neither found nor opened.

How can I assign nemo to the activities feature as well ?

Greetings,Wolf

---

### Post by #&amp;thj^% on 2022-04-04
> **drechsel said:**
> I'm using nemo instead of nautilus. I executed all the steps recommended in various articles, so most things work nice with nemo, including nextcloud integration.


EDIT: What version of ubuntu?
Show us  what has been done, >>> various articles don't tell us anything. there's lots of articles out there, some are for older releases.
if we add to what you have now, a wrong suggestion could result in more frustration for you.

---

### Post by drechsel on 2022-04-04
True - thank you. 
So - i'm on Ubuntu 20.04, and the commands I applied are these:

```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
gsettings set org.gnome.desktop.background show-desktop-icons false
gsettings set org.nemo.desktop show-desktop-icons true
```

Well, I've been dealing with Nemo so long now, it's impossible to list all the comments I applied during last years. But above ones should be the essential one. I may have read this article [https://itsfoss.com/install-nemo-file-manager-ubuntu/](https://itsfoss.com/install-nemo-file-manager-ubuntu/)

Cheers, Wolf

---

### Post by #&amp;thj^% on 2022-04-05
Thanks.
I like the majority of Abhishek's articles, that one was a good one to follow.
so when this is run in the terminal:
```
xdg-open $HOME
```
Nemo opens then, right?
and to check/verify (sometimes it's just the small things) that nemo-desktop was added in the list of startup applications. 
If still no joy please see: [https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu](https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu)
The post to pay close mind to is BOLDED.
Good Luck

---

### Post by drechsel on 2022-04-06
Thank you for your care!

> **1fallen said:**
> 
so when this is run in the terminal:
```
xdg-open $HOME
```
Nemo opens then, right? Is that a problem?
Yes, it opens But I get this message:

```
** Message: 07:22:03.545: nemo-desktop: session is not cinnamon (checked XDG_SESSION_DESKTOP,DESKTOP_SESSION environment variables.) Applying default behavior

```

In fact, I did not have nemo-desktop in startup apps, so I added ```
nemo-desktop
```

But:
Doing a `nemo-startup &` does not help - "activities" still calls nautilus. What else can I do?

Cheers,Wolf

---

### Post by #&amp;thj^% on 2022-04-06
Almost forgot you, check this file then:
```
gedit ~/.config/autostart/nemo-desktop.desktop
``` 
add with the following content: (or your needed lang support)this config is "[en_US]"
```

[Desktop Entry]
Type=Application
Exec=nemo-desktop
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Nemo Desktop
Name=Nemo Desktop
Comment[en_US]=
Comment=
```
One last suggestion, also check with Settings and select the Settings launcher. In the left pane, select Details > Default Applications. making sure Nemo is used as the file manager

---

### Post by drechsel on 2022-04-07
Thank you for your patience - very much appreciated!
My `~/.config/autostart/nemo-desktop.desktop` looks all the same - exept I have [de_DE].

In my settings, I do not see "Details > Default Applications" - I only have "Default applications", which does not offer further controls, and it is not about files. Can I activate it in dconf editor or so?

[https://www.dropbox.com/s/y1w0fpz4eyfzoqq/Bildschirmfoto%20von%202022-04-07%2007-51-39.png?dl=0](https://www.dropbox.com/s/y1w0fpz4eyfzoqq/Bildschirmfoto%20von%202022-04-07%2007-51-39.png?dl=0)

Cheers,Wolf

---

### Post by #&amp;thj^% on 2022-04-07
Well all this should of been handled from your commands shown in your first post.
Start again:
```

sudo apt install dconf-tools
gsettings set org.gnome.desktop.background show-desktop-icons false
```
now Nemo is enabled by default to draw the desktop icons. Simply, start Nemo or restart the session (log out and log in). Not yet though.
Now we set Nemo as default:
```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```
and again:
```
gsettings set org.nemo.desktop show-desktop-icons true
```
Now before you logout please check, gnome-tweak-tool & mark enabled "Have file manager handle the desktop"
When we have success I'll show how to revert to nautilus. (might not be necessary for you)

---

### Post by drechsel on 2022-04-08
> **1fallen said:**
> 
Now before you logout please check, gnome-tweak-tool & mark enabled "Have file manager handle the desktop"

I found a screenshot in the web where this control should be placed - but it's not there in my system. Such it looks:

[https://www.dropbox.com/s/rxe5pxvaipq33xi/Bildschirmfoto%20von%202022-04-08%2007-41-01.png?dl=0](https://www.dropbox.com/s/rxe5pxvaipq33xi/Bildschirmfoto%20von%202022-04-08%2007-41-01.png?dl=0)

---

### Post by #&amp;thj^% on 2022-04-08
I just can't beleive this, I set mine (Test os to see)
I followed everything I told you to; (You most likely will still **see files** but the one associated with nemo is** named Home or your Username)**
```
sudo apt install dconf-tools
gsettings set org.gnome.desktop.background show-desktop-icons false
```
then:
```
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```
then
```
gsettings set org.nemo.desktop show-desktop-icons true
```
It's been years since I last visted Gnome, so I have miss-led you a bit.
Go to Activities, and type Startup applications.
Add even if Nemo already shows there, so click add, then fill in like below:
Use>>Nemo Desktop in the Name field
Use>>nemo-desktop in the Command field
See Screenshots below to help.

You can also use the old Nemo desktop handling (non-grid) if you want, by disabling the use-desktop-grid option which also resides in org / nemo / desktop. (From dconf-editor)
EDIT: I just had a thought, when you say call from activities are you speaking about the left panel? (or where your placement of the panel is)

---

### Post by drechsel on 2022-04-09
World of computing is full of mysteries, untold secrets and conspiracy.

You pointed my attention to the "activities" menu entry. Actually, I never use it but hit the "Super" key instead. So, I once clicked the menu entry (9 dots in a square) - and like magic - nemo launches, and even better: Since then the super key launches nemo as well. For what reason ever...
One petitesse remains - not even worth to be mentioned: With activities activated, I see left hand side the (silver) nautilus icon instead of the orange nemo. But who cares...

THANK YOU SO MUCH, MAN! - I owe you a bucket of franconian country beer!

Greetings,Wolf

---

### Post by #&amp;thj^% on 2022-04-09
You did the heavy lifting, it just needed a little boot to the back-side. ;)
I wouldn't turn down your offer though. :lolflag:

---

