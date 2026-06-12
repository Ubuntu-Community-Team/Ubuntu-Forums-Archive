---
title: "I need a way to generate &quot;Nag&quot; Messages"
date: 2008-12-18
forum: General Help
---

### Post by Old_Grey_Wolf on 2008-12-18
I need a way to generate "Nag" Messages.

I have been using Linux distros long enough that I am starting to forget about the Windows boxes the family members depend on me to maintain. 

I am starting to forget about updating Windows, IE, and anti-virus software. The anti-virus software I use is free; however, the license has to be registered every 6 months apparently. I could turn on automatic Windows update and IE update but I have had problems with them messing up the computers so I prefer to wait a few days. 

What I am looking for is something I can set up to remind me to update the Windows boxes. Maybe there is something in Evolution or some other application I could use.

Any ideas?

---

### Post by ju2wheels on 2008-12-18
You can schedule something into anacron to just launch a note inside gedit or some custom script that will then remind you of those tasks....

---

### Post by kostkon on 2008-12-18
> **Old_Gray_Wolf said:**
> I need a way to generate "Nag" Messages.

I have been using Linux distros long enough that I am starting to forget about the Windows boxes the family members depend on me to maintain. 

I am starting to forget about updating Windows, IE, and anti-virus software. The anti-virus software I use is free; however, the license has to be registered every 6 months apparently. I could turn on automatic Windows update and IE update but I have had problems with them messing up the computers so I prefer to wait a few days. 

What I am looking for is something I can set up to remind me to update the Windows boxes. Maybe there is something in Evolution or some other application I could use.

Any ideas?
Yes, you could use Evolution to set up your reminders. It will use pop-ups and an icon in the taskbar to inform you about them.

---

### Post by dcstar on 2008-12-19
> **ju2wheels said:**
> You can schedule something into anacron to just launch a note inside gedit or some custom script that will then remind you of those tasks....

You can use **xmotd** to display messages, or scripts like this which I use to display a pop-up a message if a Virus is found in my incoming e-mails:

```
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

# FILE=/tmp/$$_outclam.tmp
FILE=/tmp/outclam.tmp
/usr/bin/clamscan - 1>$FILE

if [ $? -eq 1 ]; then
STRING=$(grep "FOUND" $FILE |cut -d: -f2)
/usr/bin/zenity --warning --title="Evolution: Virus detected" --text="$STRING"
exit 1
fi

exit 0
```

---

### Post by Old_Grey_Wolf on 2008-12-19
Thanks for the replies. I'll give each of them a try.

---

### Post by kerry_s on 2008-12-19
do you have a "todo" program?

i use gtodo to setup notification to do things.

---

