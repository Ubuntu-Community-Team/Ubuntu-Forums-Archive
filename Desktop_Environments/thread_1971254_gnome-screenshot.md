---
title: "gnome-screenshot"
date: 2012-05-02
forum: Desktop Environments
---

### Post by sefs on 2012-05-02
Hi there,

My gnomescreenshot current saves to my home directory which I don't like.  I alreay don't like that it does not give me the option on where to save it each time.  I would prefer a default location of my desktop.

I have gone into dconf and set the auto-save to "Desktop"  also tried "~/Desktop", but it still saves to my home directory.  

Anyway of getting it to save to the Desktop by default?

Thanks.

---

### Post by raja.genupula on 2012-05-02
it should ask . 
do this command and try again .
```
sudo apt-get install --reinstall <application_name>
```

in the app name , place that name . 

let us know what you got.

---

### Post by mc4man on 2012-05-02
The confirmation prompt is only enabled for unity*

To change location in gnome-shell you probably are using the correct schema & key  - 
 org.gnome.gnome-screenshot auto-save-directory

But not inputing location correctly. To switch to Desktop do like this, replace blue with your username

```
file:///home/[COLOR="Blue"]doug[/COLOR]/Desktop
```

---

### Post by sefs on 2012-05-02
Hi thanks all.  

The first suggestion didn't work but the second one did.  I was specifying an incorrect path as mc4man pointed out.  After using his path pattern its now saving to the desktop by default.

---

### Post by mc4man on 2012-05-02
Anyway - regarding the default autosave from keyboard screenshots in gnome
This is the LP bug, as mentioned fix released in ubuntu for unity*, open in gnome for gnome* sessions
[https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952)

---

### Post by sefs on 2012-05-02
> **mc4man said:**
> Anyway - regarding the default autosave from keyboard screenshots in gnome
This is the LP bug, as mentioned fix released in ubuntu for unity*, open in gnome for gnome* sessions
[https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/927952)

Interesting. This is the kind of thing that would give you a stroke out of pure anger.

---

