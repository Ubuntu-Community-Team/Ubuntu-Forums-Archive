---
title: "difference between starting app from menu and cmd line"
date: 2005-10-24
forum: Desktop Environments
---

### Post by coldrick on 2005-10-24
I have an app server which I start with:
sudo /opt/SUNWappserver/bin/asadmin start-domain domain1

Works fine, and returns to the command prompt. Now if I create a menu item that has that same command, it doesn't work. I've tried ticking the "Run in Terminal" box, even tried - desperation setting in - terminating the command line with an ampersand.

There's something obvious I'm missing in the difference between the two ways of running the command.

Any ideas?

Thanks and regards,
David

---

### Post by aysiu on 2005-10-24
Have you tried making the command ```
gksudo /opt/SUNWappserver/bin/asadmin start-domain domain1
```?

---

### Post by coldrick on 2005-10-24
Yes - didn't make any difference.

Regards,
David

---

### Post by aysiu on 2005-10-24
[QUOTE=coldrick]Yes - didn't make any difference.

Regards,
David[/QUOTE] You're not choosing to run the command I gave you in terminal, are you?

---

### Post by Whatsisname on 2005-10-25
same thing happens for me when I try to run matlab.

---

### Post by coldrick on 2005-10-25
Despite some combos not making sense, I've tried both sudo and gksudo both in terminal and not in terminal: none of the combinations work.

Regards,
David

---

### Post by NewWithoutClue on 2005-10-25
make a bash script with "#!/bin/bash" on the first line ( without quotes ). Place your command on the second line...then set this script to be the file thats executed from the menu click.

let me know if thiss helps.
Regards,
Paul.

---

### Post by coldrick on 2005-10-25
No joy with bash script, newwithoutclue

---

### Post by NewWithoutClue on 2005-10-25
gave it a shot, sorry.

um....good luck? lol i don't know much/enough to help you, sorry.

Paul.

---

### Post by mariuss on 2005-10-26
I had similar problems with some other apps.

In my case the problem turned out to be the fact that those apps needed some environment variables. These variables are available while running from command line, they are set in /etc/bash.bashrc, but when you run from menu or panel the environment is not the same.

The workaround I used was to write a short script in which I set these variables and then call the app.

Any clues how can you set environment variables that are generally available?

---

### Post by coldrick on 2005-10-26
That's a thought - I'll take a look.

Thanks,
David

---

