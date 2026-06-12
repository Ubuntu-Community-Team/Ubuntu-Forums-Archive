---
title: "Importing ssh keys into keyring, gnome keyring as ssh-agent"
date: 2011-01-06
forum: Desktop Environments
---

### Post by dendroid on 2011-01-06
Hello all,

I'd like to avoid ssh-add at the beginning of my session and have id_rsa and company treated like other things in my keyring (unlocked with my login password). It seems like gnome-keyring works for my network passwords and stuff, but it doesn't seem to work with ssh keys at all.

I can't get seahorse to import them, which other posts have suggested is due to their detected MIME type. "file" detects them correctly, but the freedesktop MIME database detects them as VHDL files. Why? How can I fix this? What is seahorse expecting?

Also, I noticed that if I have pgp-agent or ssh-agent installed, gnome-session will launch them. Will it still launch its own ssh-agent component, or will those replace it? (I'm not sure how it could replace ssh-agent as ssh-agent forks the rest of the session's processes, setting SSH_AUTH_SOCK in their environment.)

Finally, I heard id_rsa is supposed to get added to the keyring by default, but it doesn't seem to.

---

### Post by kongo09 on 2011-01-14
I have the same question and would appreciate help. Running Ubuntu 10.10 I'm pretty annoyed that after each reboot of the machine I need to do an ssh-add for my ssh keys in order to use them with ssh.

Is there a way for the gnome-keyring to do this for me?

---

### Post by kongo09 on 2011-01-14
Similar question, also no answer:
[http://ubuntuforums.org/showthread.php?t=1601632](http://ubuntuforums.org/showthread.php?t=1601632)

---

### Post by kongo09 on 2011-01-14
Just found something:

When I name the key file id_rsa and place it in ./ssh it is picked up and works. Before, I had named it according to the identiy it was reflecting, but that broke the process.

---

### Post by leorolla on 2011-01-14
The problem in the other thread is about LXDE session not loading the  authentication agent properly. With Gnome session I have no problems.

Seahorse works just fine with ssh keys.

It loads it self as an authentication agent and loads the key to the ssh-agent running behind your desktop session.

When you run "ssh yourdomain", ssh-agent sees the key loaded, which points to this authentication agent. This pops up a Gnome Keyring dialog where you are asked for the key passphrase, and now you have the choice to remember the passphrase for the session, forever, or forget, just like any other secret kept by Gnome Keyring, such as wireless or encrypted disks. If you ask to remember forever, it will be unlocked during login and normally you will never see the dialog again.

Of course your key files should have standard names and be placed on the standard folder, gnome-keyring will not scan your whole disk for a key. It seems that they should be named id_rsa or id_rsa.[12345...] together with a ---.pub file, and placed on ~/.ssh. If you are having problems with it finding your keys, run "seahorse" and see whether it recognizes them. You can first see if the key is on My Personal Keys, and if not, either import or create a new one. It also helps you configuring them with the hosts you want to log in.

Disclaim: I don't know how well things go together if you also want to play with pgp-agent.

---

### Post by mike-g2 on 2011-04-13
Following the instructions posted by leorolla, I have the same experience *except* when I try to ssh to another machine.  I do get the window asking for the key that corresponds to the .ssh/id_rsa key I created.  However, I am NOT given an option to unlock it once, for the session, or forever.  It just works for the current session and I want to be able to set it forever.

I wonder if I have a security option set somewhere else that's responsible for this undesired behavior.

Any one having a similar problem or have an idea about a solution?

Thanks,

Mike

---

### Post by chenel on 2011-04-28
> **mike-g2 said:**
> However, I am NOT given an option to unlock it once, for the session, or forever.  It just works for the current session and I want to be able to set it forever.


If you are using 10.10, as I am, the option is buried underneath the "details" drop-down in the box that pops up asking for your password.  Took me ages to find it...

---

