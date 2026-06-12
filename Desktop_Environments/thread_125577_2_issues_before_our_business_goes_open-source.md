---
title: "2 issues before our business goes open-source"
date: 2006-02-04
forum: Desktop Environments
---

### Post by Zelut on 2006-02-04
We are considering a migration to open source in our office but there are two issues that need to be worked out before we can do this.

1) our data entry server runs an IBM UNIX 5.3 AIX (if that means anything to anyone).  Currently we use a windows terminal emulator to login and place orders, etc.  The only issue with this is that this IBM emulation uses a IBM 3151 emulation that doesn't seem to be out-of-the-box supported by gnome-terminal.  Can anyone point me toward an emulator that can support our needs?

2) we do a live-chat-via-website with customers and use a program called Timpani now.  Its, of course, windows based, so we would need an equivalent.  I think an IRC solution would work but what do you suggest?

Thanks for the help.  I hope to be able to solve these few issues soon so we can ditch the licenses and save the bottom line.

---

### Post by kverde on 2006-02-04
On issue #2, I tested [Crafty Syntax Live Help]("http://www.craftysyntax.com/") and found it quite good.

Short description from their website:   Crafty Syntax Live Help (CSLH) is an open source live support solution that helps customer support with live help functionality that can be proactively pushed to visitors to your site or requested by the consumer. Crafty Syntax includes a large range of features to allow multiple operators, multiple departments and multiple languages to be used.

Crafty Syntax Live Help is free and is progammed in PHP with Mysql for the datatabase. Other highlighted features include the ability to create your own questions, auto inviting visitors, referer tracking, page tracking, ability to view what the customer is typing as they type, multiple chat sessions, sound alert, leave a message if offline, push urls, quick responses, Customizable graphics, and multiple operators. runs on your server and is open source GPL.

---

### Post by Zelut on 2006-02-04
Thanks for the tips on that.  This might be a great solution.  I have yet to test it on my own but one of the problems we currently have is that we only have 3 licenses (can I just say how much I hate software licensing?)  With this free solution we can have as many users as we need.  This could be great!

I'm sure it'll take a little bit of a learning curve to migrate everyone from one to another but thats what working is all about right?  Doing whatever the boss tells you to do :)

Thanks agian

---

### Post by kverde on 2006-02-04
Also, by the way, installing Crafty Syntax is A SNAP if you have a webhost that uses "Fantastico".  Basically, you click INSTALL and it is installed.

---

### Post by az on 2006-02-04
1.  I don't know what the differences are between the terminals, but I am certain there is a simple solution.  Linux boxes talk to other Unix boxes all the time.  I am sure there is an emulator or a setting for this somewhere.

2.  I run a site that uses  Drupal (a CMS that run on php).  There is a Drupal plugin for a chatbox.  It works pretty well.  I'm certain there are other php implementations of the chatbox or similar features.

---

### Post by Gort32 on 2006-02-04
**x3270** is a full-featured terminal emulator that should do what you need.  I use it to connect to my IBM AS/400 system

---

