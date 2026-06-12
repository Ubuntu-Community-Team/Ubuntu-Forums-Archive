---
title: "limewire 4.12.3 pro"
date: 2006-07-12
forum: Desktop Environments
---

### Post by blu.gecko on 2006-07-12
my subscription just expiried, I installed the new 6.0.6 ubuntu and I tried installing limewire like you do in ubuntu version's 5.0.4/5.10

sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh

Insert the following lines into the new file 

cd /opt/LimeWire/
./runLime.sh

Save the edited file 

sudo chmod +x /usr/bin/runLime.sh
sudo gedit /usr/share/applications/LimeWire.desktop

Insert the following lines into the new file 

[Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;

and ofcourse add JRE1.5, but this doesnt work anymore.....
so how do you install it now?

---

### Post by taurus on 2006-07-12
Use Frostwire, [http://www.frostwire.com/](http://www.frostwire.com/)...

---

### Post by easyease on 2006-07-12
or try Gtk-gnutella and be blown away by fast downloading speed and very low cpu usage.

---

### Post by blu.gecko on 2006-07-12
Thank you for your replies, but I want to know how to install LimeWire Pro which I have purchased......

---

### Post by easyease on 2006-07-12
Frostwire is exactly the same as Limewire Pro mate(its just the open source, free version). and its very easy to install using Automatix. Honest Limewire is crapolla.

---

### Post by Maheriano on 2006-07-15
How do I install Limewire or Frostwire? I couldn't find either in the package lists. And for some reason I can't su to root to emerge it.

---

### Post by visvak on 2006-07-15
actually its pretty install Limewire, use Alien

Open up terminal and type -

```
sudo alien "the full name of the limewire package inclding the .RPM bit"
```

now alien will generate a .DEB package in the same directory were the old .RPM was. just double click it and it will install.

---

### Post by taurus on 2006-07-16
> **Maheriano said:**
> How do I install Limewire or Frostwire? I couldn't find either in the package lists. And for some reason I can't su to root to emerge it.

Did you see the link I provided in my original message?  Click on the Ubuntu/Debian version and save it to your computer.  Then, install it with dpkg command!!!

```

cd ~/Desktop
sudo dpkg -i FrostWire-4.10.9-2.i586.deb

```

---

### Post by Maheriano on 2006-07-16
None of those links work, dude. I get a error. > XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 1:y, currentValue, mimeLiteral);
^

---

