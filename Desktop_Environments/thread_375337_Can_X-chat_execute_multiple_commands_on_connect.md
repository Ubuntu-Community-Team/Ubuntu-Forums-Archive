---
title: "Can X-chat execute multiple commands on connect?"
date: 2007-03-03
forum: Desktop Environments
---

### Post by Janzuka on 2007-03-03
Hi,

When i connect to an irc server, x-chat can be set to execute commands when connecting ( you know, for instance to auth when logging on to Quakenet). However, i wish it could execute more commands upon connecting the network. It just seems impossible: i've tried to make it work by separating the commands with various punctuation marks - unsuccessfully. ](*,) 
So if someone knew how to do this, i would appreciate your advice :) 

Janne

---

### Post by invalid on 2007-03-03
I am not an X-Chat user, but what about creating an alias or script that runs the commands, and simply calling that on connect?

---

### Post by shirilover on 2007-03-03
Yes, X-Chat can execute multiple commands when connecting to a network.
First, create a text file with one command per line. This can authenticating, setting modes, joining channels, etc.
Edit the properties for the network you created. In the space for command to execute use -- LOAD -e /path/to/textfile
Now, when you connect to this network, the commands in the text file will be executed.

More information about this can be found [here]("http://www.xchat.org/faq/#q214")

---

### Post by Janzuka on 2007-03-04
Thanks guys!

I created a text file and made x-chat load the commands written in the file, and,  to my delight, everything works perfectly. :cool:

---

