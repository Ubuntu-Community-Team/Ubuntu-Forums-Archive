---
title: "Question about Telnet (server)"
date: 2009-03-04
forum: General Help
---

### Post by Noxn on 2009-03-04
Did you ever see the Starwars in ASCII? No? You should!
"telnet towel.blinkenlights.nl 23" (Without "")

I wanted to know how to make a Telnet server that DOES something, instead of being some kind of remote terminal thing.
Like executing a script or something. (Like blinkenlights)


(I'm asking here because much of what Google finds is about using it for remote stuff / why you shouldn't use telnet for remote stuff)
(Also, sorry if this is wrong forum or something, I don't now where it should go.)



EDIT:
As some guys dont understand what i want, i will explain it again:
"I want a telnet server that >IS NOT< for remote connecting, but for Doing something, like a MUD, or hosting something similar to that starwars film."

---

### Post by smokegfx on 2009-03-04
sweet, though whats the use?

---

### Post by albandy on 2009-03-04
telnet is insecure, all your passwords and data are transfered in plain text, I recomend you to use ssh.
Simply install ssh.
sudo apt-get install ssh
To connect to your computer from remote: ssh myusername@mycomputerip

---

### Post by smokegfx on 2009-03-04
or
sudo apt-get install openssh-server :)

---

### Post by Noxn on 2009-03-04
I do NOT want to remote connect or anything like that.
Read my post.


Or, if i didn't explain it good enough:

I want a telnet server that IS NOT for remote connecting, but for Doing something, like a MUD, or hosting something similar to that starwars film.

---

### Post by Noxn on 2009-03-04
Any one? please?

---

### Post by Nepherte on 2009-03-04
By definition, telnet is a network protocol and provides access to a remote machine. I don't see how you would want to use use telnet for anything else since that's the only thing it does. You probably want another application.

---

### Post by vociferous666 on 2010-12-22
wow can u guys get and dumber....

he wants to host a telnet server that is locked into its own shell and directory for the simple purpose of doing something entertaining and interesting. kinda like a quake server or CS server.

i cant believe how many retards simply direct ppl to ssh.
what if we dont need to be secure???
what if ssh is too cumbersome for the simple task at hand???
what if i only want to connect locally for simple administrative tasks on a secure network i.e. no wireless.

why is everyones first answer SSH!!!!!!

and why the hell are there so many versions of telnet and none of them siple to install????

by mere luck and going throgh 4 diff telnet servers, i finally got it installed and almsot 100% working on my old media server.

and NO the telnet server was not forwarded to the internet.
u guys have to give us newbs a LITTLE bit fo credit.

hows about a due warning and then directing us how to do what we asked??

why is it so difficult to get something as simple as telnet up and runing!!??

/rant

---

