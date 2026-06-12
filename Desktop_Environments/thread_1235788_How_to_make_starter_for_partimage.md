---
title: "How to make starter for partimage"
date: 2009-08-09
forum: Desktop Environments
---

### Post by FScheltens on 2009-08-09
Hello,

i'm trying to make a starter for partimage in Ubuntu, because i use this command to make a backup of my main pc, and i don't want to forget which command i need to use for it.
However, partimage needs root permission to run properly. So which command do i need to put in a starter to make partimage run with root permission?
I haven't been able to with sudo, gksudo or gksu, so i'm obviously doing something wrong.

---

### Post by gjoellee on 2009-08-09
Tried ```
sudo -i
```
????

I am not sure what a "partimage" is, so maybe if you could post the command you're using so I can have a look at it?

Although I can't tell you have to become root with an other command because that would be not following the forum rules.

---

### Post by gjoellee on 2009-08-09
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

---

### Post by FScheltens on 2009-08-24
Ok i tried sudo -i and it doesn't seem to work. What i want is this:
I can easily start a terminal window and enter the command "sudo partimage", and that works fine.
What i want is to make a starter on my desktop that does the same thing from the gui. As in:

[IMG]http://i558.photobucket.com/albums/ss25/FScheltens/1251137836.png[/IMG]

So what is the correct command that goes on the "command" line?

@ gjoellee: Thanks for the help so far but this is really a x-server / shell issue not a partimage issue.

---

