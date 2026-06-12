---
title: "Gaming FRUSTRATION - Cedega - [Errno 13] Permission denied"
date: 2009-04-27
forum: Gaming &amp; Leisure
---

### Post by markackerman8@gmail.com on 2009-04-27
Gaming FRUSTRATION - Cedega - [Errno 13] Permission denied

as a last ditch attempt at running games in ubuntu I have managaed to get Cedega and it comes up with 

"An error was encountered while creating the folder: [Errno 13] Permission denied"

Is there a simple fix for this or any other waqys to get games working other than wine and cedega???

I dont want to go back to windows for CoD4

Please and thanks

---

### Post by Perfect Storm on 2009-04-27
How are you installing it? Do you have permission to install it on the computer you're at?

Try give us some more info ;)

---

### Post by ELD on 2009-04-27
Going to need more info than that, does it happen while running it, installing it?

If installing where are you installing it to.

We have nothing to go on to help you right now.

---

### Post by equity on 2009-05-16
> **markackerman8@gmail.com said:**
> Gaming FRUSTRATION - Cedega - [Errno 13] Permission denied

as a last ditch attempt at running games in ubuntu I have managaed to get Cedega and it comes up with 

"An error was encountered while creating the folder: [Errno 13] Permission denied"

Is there a simple fix for this or any other waqys to get games working other than wine and cedega???

I dont want to go back to windows for CoD4

Please and thanks
I got the exact same problem when I wanted to install WarCraft_III on Debian unstable.
Issuing the following command should solve it:
$ chmod 777 /home/<username>/.cedega -R

Greetings.

---

### Post by revoice on 2010-05-16
thx that command worked for me too.

may i know what the 777 is for?

---

### Post by ELD on 2010-05-16
> **revoice said:**
> thx that command worked for me too.

may i know what the 777 is for?

It's the attributes of the file, so who can read, write and execute it.

777 meaning everyone basically.

---

