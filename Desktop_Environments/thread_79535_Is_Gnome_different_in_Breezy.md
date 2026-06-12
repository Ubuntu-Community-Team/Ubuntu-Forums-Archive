---
title: "Is Gnome different in Breezy?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by blu.gecko on 2005-10-20
in the new ver 5.10 did they kill the old gnome look?
and are the backports up yet, I havent seen a new ubuntuguide out yet for 5.10.

I cant decide if I want to jump ship from 5.04 to 5.10:rolleyes:

---

### Post by Hairy_Palms on 2005-10-20
gnome looks exactly the same, the only bad change ive seen is they got rid of the run applications button the main menu :(

---

### Post by KingBahamut on 2005-10-20
No they did not. 

Looks like good ole gnome.

---

### Post by blu.gecko on 2005-10-20
run applications I can deal with Start-Run it reminds me to much of MS, what about backports? reason I ask is I want to get my java and limewire back up soon. me and a hand full of buddies share file directly through ip lime sharing

---

### Post by KingBahamut on 2005-10-20
Those are easily installed. 

Blackdown Java is available through the repositories and the Add Applications app. 

Limewire is a relatively easy install you can use the below procedure for that. 

> wget -c [http://frankandjacq.com/ubuntuguide/LimeWireOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireOther.zip)
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh

> # Insert the following lines into the new file

cd /opt/LimeWire/
./runLime.sh

# Save the edited file (sample)
#

sudo chmod +x /usr/bin/runLime.sh
sudo gedit /usr/share/applications/LimeWire.desktop

> Insert the following lines into the new file

[Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;

---

### Post by blu.gecko on 2005-10-20
[QUOTE=Hairy_Palms]gnome looks exactly the same, the only bad change ive seen is they got rid of the run applications button the main menu :([/QUOTE]

Ok, I just installed 5.10 but gnome is not exactly the same, they commercialized it, I now have a ubuntu icon for my application drop down, they did away with the gnome icon, so how do I get that back, im picky yes but I like my gnome like that.:confused:

and the run function, they didnt kill it all together, just add it to the pannel gnome pannel, edit menu, add menu, add it to the application system tools, cant remember the commands though, might pull out a copy of 5.04 live and pull all the info from that and add it to your pannel.

food for thought

---

### Post by KingBahamut on 2005-10-20
I would hardly call an ubuntu icon in the menu bar anything remotely close to "commercialized". I would however call it "distribution specific". I dont see that as an issue. 

as far as the Run application item i believe its 

apt-get install gnome-run I believe.

---

### Post by blu.gecko on 2005-10-20
king bahamamut,

you said Those are easily installed.

Blackdown Java is available through the repositories and the Add Applications app.

Limewire is a relatively easy install you can use the below procedure for that. 

I went to try sudo apt-get install sun-j2re1.5 and ofcourse it didnt work becuse the backports got changed when 5.10 came out, i looked up blackdown java and java, and the java release 5 isnt in the package manager, so how do I get suns java release version 5, I tried the wiki section when I was using 5.04 after they killed the backport but I didnt quite understand the installation process, before I came to ubuntu I came from rpms and such.....

---

### Post by KingBahamut on 2005-10-20
Add Applications > Internet > More Applications > Java Webstart or such, it will ask you to enable a repo, you of course desire to do so. 

Install and have at it.

---

### Post by blu.gecko on 2005-10-20
I suppose there is no way to get rid of the distro friendly icon and get my gnome icon back?

I know its petty....but thats the way I like it.

:rolleyes:

---

### Post by blu.gecko on 2005-10-20
[QUOTE=KingBahamut]Add Applications > Internet > More Applications > Java Webstart or such, it will ask you to enable a repo, you of course desire to do so. 

Install and have at it.[/QUOTE]

I installed it but It never asked me any questions...... limewire wont load, how do I fix it?


NEVERMIND, I reinstalled it, works gret now

---

