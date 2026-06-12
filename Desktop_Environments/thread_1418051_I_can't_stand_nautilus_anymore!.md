---
title: "I can't stand nautilus anymore!"
date: 2010-02-28
forum: Desktop Environments
---

### Post by hakermania on 2010-02-28
Nautilus begun showing problems while I had Transmission open and I was seeding:It started not to respond and again and again.Now it becomes worse.When I start my pc, I want to do a folder named "shared" and located on my desktop shared.But when I am going to its properties and push the "Create Share" button nautilus is not responding. I have decided to install an other file browser.What I want is to give me detailed instructions on how to install an other file browser like dolphin, because the last time I did something like this (I mean to unistall nautilus and install dolphin) after a reboot the pc could't boot and I continued with a format.
So, please be 150% sure on what you will answer right now!
Ah, and special thxs for any answers!

---

### Post by hakermania on 2010-02-28
Guys I really can't stand it!
Plz help me!
I don't know what else to do!
I am thinking of returning back to windows but I've really loved ubuntu and I don't really want to return back for such a useless, for somebodies, problem!!!
PLZ HELP!!!

---

### Post by chewearn on 2010-02-28
I can't help you much on the nautilus problem. But on file sharing (using samba), I suggest use the package called [system-config-samba]("apt://system-config-samba").  I find it works better that the one built-in nautilus (though not as straight forward).

After installation, you find the app in:
System > Administration > Samba

---

### Post by hakermania on 2010-02-28
Yeah, ok but Nautilus does generally "stacks".
I want an other file browser and quickly!!

---

### Post by hakermania on 2010-02-28
Help guys!!!!
HELP HELP HELP!!!!

---

### Post by chewearn on 2010-02-28
Well, I am partial to dual pane file manager, and use Krusader as the main file manager instead of Nautilus.  It's a KDE app though, so it doesn't integrate fully into Gnome (in terms of look and feel).

---

### Post by theozzlives on 2010-02-28
Ummmm... do you get an error when you try to  create a share? Also, it's recommended that you wait 24 hrs before bumping a thread.

---

### Post by Alexandre Putt on 2010-02-28
You can simply install Dolphin (or any other file manager) using Synaptic. It will bring with itself a number of dependencies. There should be no problem with this.

I don't know how to make it default for viewing folders, though, but it should be possible. 

Uninstalling Nautilus was a bad idea.

---

### Post by hakermania on 2010-02-28
Sorry about this but it is very hard for me!
No, it doesn't come up with an error.It just becomes grey - means not responding when I push the "Create Share" button!
And as I said before it is not the only issue with Nautilus.That's why i do need another file browser!

---

### Post by theozzlives on 2010-02-28
WAIT! I missed that one. You don't uninstall Nautilus. That can bork up your whole GNOME desktop. Why don't you try KDE:
```
sudo apt-get install kubuntu-desktop
```
it may be more what you're looking for.

---

### Post by mikewhatever on 2010-02-28
Well, of cause Nautilus acts up, I mean, you can't stand it, and it's very sensitive. Like it a little and see what happens.:)

---

### Post by genjix on 2010-02-28
use KDE. it's a better desktop

---

### Post by hakermania on 2010-02-28
> **theozzlives said:**
> WAIT! I missed that one. You don't uninstall Nautilus. That can bork up your whole GNOME desktop. Why don't you try KDE:
```
sudo apt-get install kubuntu-desktop
```
it may be more what you're looking for.
Yaeh ok, I installed this but how will I get rid of nautilus without crashing my whole desktop?(Something that hapened a couple of months ago....:( )

---

### Post by hakermania on 2010-02-28
Well, I installed what genjix said BUT, a big BUT I want these:
1:Unistall Nautilus without my system to be crashed
2:Tell me how to change the "Open with" option in dolphin!
3:How to do dolpphin default
4:Thx!

---

### Post by VCoolio on 2010-02-28
Uninstalling nautilus is not a good idea, because it also draws your desktop and also you may get issues when you upgrade to the next ubuntu release. Just use another file browser like dolphin or the latest thunar.

To make it the default file browser may be a bit difficult. An easy trick is to point the nautilus launcher to your file browser instead. In the following files use "sudo nano <file>" or "gksudo gedit <file>" to change the "exec=" part to whatever file browser you want:
/usr/share/applications/nautilus-home.desktop
/usr/share/applications/nautilus-folder-handler.desktop
/usr/share/applications/nautilus-browser.desktop

---

### Post by hakermania on 2010-03-02
Hm.I let you know if my dolphin did really become my default because I have noy very time right now!

---

