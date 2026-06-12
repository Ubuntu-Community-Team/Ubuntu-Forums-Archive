---
title: "ClamAV and Evolution, it can be done!"
date: 2005-10-31
forum: Desktop Environments
---

### Post by dcstar on 2005-10-31
Just searched through some previous threads and found out how to make Evolution use ClamAV to scan all incoming e-mails, have a look at:

[http://linux.togaware.com/survivor/Viruses.html](http://linux.togaware.com/survivor/Viruses.html)

It works fine for me on a EICAR virus test file attachment!

---

### Post by binarymelon on 2005-11-09
It turns out it's very difficult to send yourself a virus to test if this works.  Does anyone know of some easy methods apart from installing sendmail?

---

### Post by dcstar on 2005-11-11
[QUOTE=binarymelon]It turns out it's very difficult to send yourself a virus to test if this works.  Does anyone know of some easy methods apart from installing sendmail?[/QUOTE]
Just download an EICAR test file and use Evolution to e-mail it to yourself as an attachment.

---

### Post by binarymelon on 2005-11-14
Yeah I tried that, but the messages never make it through.  Maybe my ISP's mail server is just detecting it as a virus and not letting it through.

---

### Post by dcstar on 2005-11-15
[QUOTE=binarymelon]Yeah I tried that, but the messages never make it through.  Maybe my ISP's mail server is just detecting it as a virus and not letting it through.[/QUOTE]
Quite possible, there are ClamAV test files in Synaptic, install them and test again.

---

### Post by dcstar on 2005-12-28
[QUOTE=dcstar]Just searched through some previous threads and found out how to make Evolution use ClamAV to scan all incoming e-mails, have a look at:

[http://www.togaware.com/linux/survivor/Viruses.shtml](http://www.togaware.com/linux/survivor/Viruses.shtml)

It works fine for me on a EICAR virus test file attachment![/QUOTE]
And as a slight modification on the theme, here is a script I found that pops up a notification of what particular Virus was found in an e-mail:

Some reminders, make the script with 777 permissions, and change clamdscan to **clamscan** if you don't use the (faster) clamd daemon on your system:


#!/bin/bash
# Fred Blaise <chapeaurouge AT madpenguin DOT org>
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston,
# MA 02111-1307 USA

FILE=/tmp/$$_outclam.tmp
clamdscan - 1>$FILE

if [ $? -eq 1 ]; then
STRING=$(grep "FOUND" $FILE |cut -d: -f2)
zenity --warning --title="Evolution: Virus detected" --text="$STRING" &

exit 1
fi

exit 0

---

### Post by tnilsson on 2005-12-30
I feel a bit stupid, I can not figure out how to configure evolution according to the guide [http://www.togaware.com/linux/survivor/Viruses.shtml](http://www.togaware.com/linux/survivor/Viruses.shtml)

Can someone give some screens shoots?

---

### Post by dcstar on 2005-12-30
[QUOTE=tnilsson]I feel a bit stupid, I can not figure out how to configure evolution according to the guide [http://www.togaware.com/linux/survivor/Viruses.shtml](http://www.togaware.com/linux/survivor/Viruses.shtml)

Can someone give some screens shots?[/QUOTE]
Attached is my message filter rule - this is the first filter in my list!.

You need a script with 777 permissions (somewhere) on your system (as you can see mine is in /usr/local/bin), and a working ClamAV setup.

You can search (and download) test EICAR virus files to check if ClamAV is working, and them e-mail them to yourself to test your Evolution script.

---

### Post by tnilsson on 2005-12-31
Thank you for the fast reply! :-)
This is why I like the ubuntuforums!

Happy New Year.

---

### Post by VR6Pete on 2005-12-31
send a blank email to...
[email]virus.echo@mimesweeper.com[/email] (delivers an eicar false positive)
[email]exe.echo@mimesweeper.com[/email] (delivers a uue encoded small exe file)
[email]doc.echo@mimesweeper.com[/email] (delivers a uue encoded word doc)
[email]image.echo@mimesweeper.com[/email] (delivers a uue encoded image file)
[email]encrypt.echo@mimesweeper.com[/email] (delivers a password protected zip file)
[email]vbs.echo@mimesweeper.com[/email] (delivers a harmless VB script file)
[email]threat.echo@mimesweeper.com[/email] (delivers the trigger text (only) of the sircam virus)
[email]spam.echo@mimesweeper.com[/email] (delivers a test spam message)

---

### Post by davidakachaos on 2006-05-08
> **dcstar]And as a slight modification on the theme, here is a script I found that pops up a notification of what particular Virus was found in an e-mail:

Some reminders, make the script with 777 permissions, and change clamdscan to **clamscan** if you don't use the (faster) clamd daemon on your system:


#!/bin/bash
# Fred Blaise <chapeaurouge AT madpenguin DOT org>
# This program is free software said:**
> ; then
STRING=$(grep "FOUND" $FILE |cut -d: -f2)
zenity --warning --title="Evolution: Virus detected" --text="$STRING" &

exit 1
fi

exit 0
And how to add this to evolution virus scanning .pl file? (I know, n00p question....)

---

### Post by dcstar on 2006-05-19
[QUOTE=davidakachaos]And how to add this to evolution virus scanning .pl file? (I know, n00p question....)[/QUOTE]
This has nothing to do with the .pl file, it is used in the method described above (the original web site has apparently changed just to give instructions for the .pl method).

---

### Post by deepspring on 2006-07-08
thanks for this!

rofl!

I'm actually having a tough time testing this... my ISP automatically scans all incoming emails.

---

### Post by geezerone on 2006-10-06
> **VR6Pete said:**
> send a blank email to...
[email]virus.echo@mimesweeper.com[/email] (delivers an eicar false positive)
[email]exe.echo@mimesweeper.com[/email] (delivers a uue encoded small exe file)
[email]doc.echo@mimesweeper.com[/email] (delivers a uue encoded word doc)
[email]image.echo@mimesweeper.com[/email] (delivers a uue encoded image file)
[email]encrypt.echo@mimesweeper.com[/email] (delivers a password protected zip file)
[email]vbs.echo@mimesweeper.com[/email] (delivers a harmless VB script file)
[email]threat.echo@mimesweeper.com[/email] (delivers the trigger text (only) of the sircam virus)
[email]spam.echo@mimesweeper.com[/email] (delivers a test spam message)

Thanks for the test msgs if only my ISP didn't block them ;) but glad they do and it works for them.

I wasn't sure about using the perl file so anyone have an idiots guide? Instead I tried synaptic and added clamassassin and clamcour but haven't tried it yet, suppose it isn't something that runs manually though or is it?

Thanks

---

