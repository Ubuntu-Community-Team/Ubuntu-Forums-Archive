---
title: "Radiance theme stopped working"
date: 2010-07-11
forum: Desktop Environments
---

### Post by mafiaspidey on 2010-07-11
Hi,

After the recent update on ubuntu 10.04, Radiance theme doesn't work. I have the murrine 0.90.3 installed. What else should I check?

thank you. Help much appreciated.

---

### Post by mafiaspidey on 2010-07-12
Solved it.

I forced version in the light-themes package from "lucid update" to "webup8". I guess the new light themes version 1.6.6 doesn't work. Webup8 version version works once I forced it.

To force a version in a package in synaptic package manager, do the following:

select the package
click "package"
In the drop down menu, select force version and select your version.

So, now that problem is solved. Next problem is bad font in QT apps such as skype and vlc. WHAT do I do???

---

### Post by mafiaspidey on 2010-07-12
Solved the qt4 font problem, too. I specified the following in my .fonts.conf:

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<match target="font">
		<edit name="rgba" mode="assign">
			<const>rgb</const>
		</edit>
		<edit name="antialias" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>hintfull</const>
		</edit>
		<edit name="hinting" mode="assign">
			<bool>true</bool>
		</edit>
	</match>
</fontconfig>

That solved it.

Thank you (to myself and the thread "[SOLVED] Qt fonts not being antialiased").

---

