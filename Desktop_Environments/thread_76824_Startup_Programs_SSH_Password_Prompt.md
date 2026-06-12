---
title: "Startup Programs: SSH Password Prompt"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Pig Monkey on 2005-10-15
(I'm posting this in the Desktop forum because I think it's a problem with Gnome, not SSH).

I have the following command in my startup programs to tunnel my outgoing mail through SSH (the same command worked fine in 5.04):
```
ssh -f -N -L 9999:mail.myserver.com:25 myserver.com -l user
```
(where myserver.com is my server, and user is my username)

When I login in to Gnome, I'm asked for my password for [email]user@myserver.com[/email]. This is a problem in itself, because I'm using SSH keys, not passwords. What's even stranger is that typing in both the password or the passphrase for the key doesn't work.
If I hit enter 5-6 times to make the pass prompt give up, I can open up a terminal copy/paste the exact command from the startup programs into the terminal, hit enter, and I'm prompted for my passphrase, as I should be. After entering in the passphrase, everything works fine.

Why am I prompted for a password? Why doesn't it like the correct password?

---

### Post by greymoose58 on 2005-10-17
I'm having the same problem when I try to ssh in manually to set up the keys. I did a clean install of Breezy and went to reset my ssh tunnel (which worked fine under Hoary) and now I can't get in at all.

I'm geting out of my depth here. Ideas anyone?

---

### Post by Pig Monkey on 2005-10-17
Looking under "Current Session" in the Sessions program, I found the ssh command had single quotes around my username. Yet the command in "Startup Programs" has no such quotes. So, I just removed the command from Startup Programs, retyped it by hand, and it seems to work now.

---

### Post by greymoose58 on 2005-10-17
Thanks Pig Monkey. Please excuse my ignorance but the Sessions program? Where do I find that?

Cheers.

---

### Post by GeneralZod on 2005-10-17
Are you sure you are using keys instead of passwords? In my experience, you have to disable both password authentication *and* challenge-response authentication in your sshd_config to achieve this.

Obviously, don't try this unless you have physical access to your server so you can restore you sshd_config if you mess up :)

---

### Post by Pig Monkey on 2005-10-17
[QUOTE=greymoose58]Thanks Pig Monkey. Please excuse my ignorance but the Sessions program? Where do I find that?

Cheers.[/QUOTE]

System --> Preferences --> Sessions
But I don't think that's going to do anything for you, if your problem is trying to SSH in manually. That's for running programs at login.

When you say you're having trouble trying to "ssh in manually to set up the keys" do you mean you're having trouble uploading the id_rsa.pub?

---

### Post by greymoose58 on 2005-10-17
[QUOTE=Pig Monkey]

When you say you're having trouble trying to "ssh in manually to set up the keys" do you mean you're having trouble uploading the id_rsa.pub?[/QUOTE]

I've managed to upload the id_rsa.pub because I sould SSH in when I started out setting up the tunnel. When I set an SSH tunnel up in Hoary (after much googling and messing around) I had to enter the password the first time I opened the tunnel. That is where I am up to. If I try to SSH in manually now it refuses the password. 

Do I have to reset something if I have too many failed password attempts?

I tried the settings GeneralZod suggested to no avail.  (Thanks for the suggestion, though.)

Cheers.

---

### Post by Pig Monkey on 2005-10-18
There shouldn't be anything to reset.

After you upload your id_rsa.pub to ~/.ssh on the server, it shouldn't be asking for your password at all, only your passphrase. Have you tried typing that into the pass prompt?
I'd try making sure you are SSHing in as the correct user (specify it with -l) and that keys are enables on the server's sshd_config.

---

### Post by greymoose58 on 2005-10-27
Thanks for the suggestion. I was attempting to set this up to access a machine where the motherboard wasn't always recognising the keyboard. Unfortunately it seems to not want to see it at all now so I can't check out any settings etc. 

Oh well, you win some, you lose some. :) 

Cheers.

---

