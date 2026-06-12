---
title: "Very annoying SSH problem that makes no sense..."
date: 2009-03-21
forum: General Help
---

### Post by sekinto on 2009-03-21
When I connect to this one server using Places > Connect to Server (SSH) I have this really weird problem. When I create a folder its owner becomes another user on this computer and not myself... it doesn't make any sense.

---

### Post by skydiver|goose on 2009-03-21
strange... you're not logged into the server as root or have a strange set of permissions on the server, do you?

---

### Post by sekinto on 2009-03-21
I don't know. My friend runs the server, all I know about it is that it runs Ubuntu Server (from an Apache message). He just gave me the info to connect (username, password, address and port).

---

### Post by The Cog on 2009-03-21
Makes me wonder about user ID numbers. If you get a terminal login, the command **ls -l** lists files with usernames, and **ls -ln** lists them by ID. Might give a clue.

---

### Post by Slim Odds on 2009-03-21
> **The Cog said:**
> Makes me wonder about user ID numbers. If you get a terminal login, the command **ls -l** lists files with usernames, and **ls -ln** lists them by ID. Might give a clue.

Yes, and try **id** also

---

### Post by sekinto on 2009-03-21
Okay, I totally get why it is doing this now.

On the server there are two accounts:
(my friends account), id: 1000
(my account), id: 1001

On my computer there are two accounts:
(my account), id: 1000
(another person's account), id: 1001

But it doesn't make sense why Ubuntu would put these two together, since the computer is not local and therefor you can have accounts with the same IDs. Is there any way to get Ubuntu to stop making this mistake, I would like to be treated as user 1001 while I'm connected to the server since that is the account I am logging into.

---

### Post by The Cog on 2009-03-22
I guess it hinges on whether the file ownership is transferred using the owners textual name or the owners ID number. Who seems to own the new directory if you use an SSH coneole login? My guess is that on the remote machine, the folder has owner 1001 and your username. I also guess that when nautilus displays it, it is fetching the directory owner by ID (1001) and then using your local PC configuration to look that ID up into a name for display.

---

### Post by sekinto on 2009-03-22
Is there any way to tell Nautilus to ignore ownership in certain folders or at least use a different configuration in those folders? This seems to only be a problem with Nautilus.

---

### Post by The Cog on 2009-03-22
Not that I know of. But I think it's only really a display issue - presumably the actual ownership on the box is correct - just displaying the wrong owner when your remote SSH in nautilus?

---

