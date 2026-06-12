---
title: "Help! Can't access screenlets from China"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by Jhongy on 2007-07-23
Hello ---

Unfortunatley the server that hosts the screenlets repository appears to be blocked in China.

Does anyone know of a mirror (or can anyone else host the repo)... or can onyone provide the relevant .debs?

Thanks in advance!!!

John

---

### Post by Espreon on 2007-07-23
Okay here are my solutions:

Option 1: Move
Option 2: Use Tor+Privoxy: so you can access the server and download the .debs
Option 3: I can e-mail you the .debs if you temporarily put your e-mail address on the post. (To avoid e-mail address harvesters put the address in this format: soinso (at) blahblah (dot) com

---

### Post by hyperair on 2007-07-23
You could also PM him or me the addresses. I have the debs too. When you get them put them into the folder called "/var/cache/apt/archives". You'll have to open that folder as root. Can be done by this command in the run dialog: ```
gksu "nautilus /var/cache/apt/archives"
```

After that just install it from Synaptic Package Manager or from the command line: ```
sudo apt-get install screenlets
```

---

### Post by Espreon on 2007-07-23
or you could just fire up a terminal and enter:

```
sudo dpkg --install (drag and drop all the screenlets files here)
```

---

### Post by Jhongy on 2007-07-23
Thanks very much guys ----- (removed).  (no brackets or square brackets)

:-)

---

### Post by Espreon on 2007-07-23
I just sent them to you, now you can remove your address.

---

### Post by Jhongy on 2007-07-23
Thanks very much :-)

---

### Post by hyperair on 2007-07-23
IF you use GNOME, just double click on the deb's. They'll open in the GDebi Gtk program or sometihng of that sort.

---

### Post by Jhongy on 2007-07-24
Thanks!

I got it installed, and got some pretty niftey desklets

Now I just need to figure out:

-- Why the settings never 'save' each time. I get them set up just right 'stay behind', 'stuck to workplaces', and upon reboot, they stay on top, and are nto stuck to all workplaces, even though the options haven't changed. I have to untick the options, and then tick them again for them to take effect again (only to lose them again at the next reboot!) Any ideas???

-- Why either of the RSS  screenlets completely crashes screenlets -- irrevocably until I restart.

---

### Post by hyperair on 2007-07-24
I'm not sure about the RSS screenlet, doesn't give me problems not that I use it anyway, but you must get screenlets to start AFTER Compiz/Beryl/Compiz Fusion has started.

---

### Post by Jhongy on 2007-07-24
Thanks....

I noticed that -- I was getting a huge gnome start-up delay when screenlets were set to start in my sessions file. The gnome splash would show for ages.

So I tred creating a script as follows:
 #!/bin/sh
beryl-manager &
sleep 20
screenletsd start &


and added it to my session.

This seems to be doing the trick.....

---

