---
title: "Limewire"
date: 2005-11-10
forum: Desktop Environments
---

### Post by microo on 2005-11-10
Can someone tell me how to remove Limewire.

Thank you

---

### Post by manicka on 2005-11-10
how did you install it?

---

### Post by microo on 2005-11-10
I  install it the way the Ubuntu Guide show me.


Microo

---

### Post by manicka on 2005-11-10
[QUOTE=microo]I  install it the way the Ubuntu Guide show me.
[/QUOTE]
Which is?, could you give me a brief run down of what you did?

---

### Post by microo on 2005-11-10
This is the way i have installed it:


wget -c [http://frankandjacq.com/ubuntuguide/LimeWireOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireOther.zip)
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.shInsert the following lines into the new file 
cd /opt/LimeWire/
./runLime.shSave the edited file (sample) 
sudo chmod +x /usr/bin/runLime.sh
sudo gedit /usr/share/applications/LimeWire.desktopInsert the following lines into the new file 

[Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;Save the edited file (sample)

---

### Post by manicka on 2005-11-11
What version of Limewire is it that you've downloaded from frankandjacq.com. I'd be inclined to get the official release and use that.

Better still, with LimeWire imposing new filters on searches, give [FrostWire]("http://www.frostwire.com/index.php?title=Main_Page") a go. I had success downloading and aliening the rpm. Works well :)

---

### Post by microo on 2005-11-11
But the thing that i want to know is how to uninstall it ?


Thanks

---

### Post by manicka on 2005-11-11
[QUOTE=microo]But the thing that i want to know is how to uninstall it ?
[/QUOTE]
Sorry, I was getting mixed up with another thread.

Limewire exists in it's own directory so just deleting the directory you created in opt should do it. Then remove the LimeWire.desktop entry you made in /usr/share/applications/.

I'm a bit lazy and would do this all in nautilus as root

```
sudo nautilus
```

I'm sure others could advise you on doing it via the CLI.

---

### Post by microo on 2005-11-11
Thanks Manicka, again i've learn things from Linux. 

Microo

---

