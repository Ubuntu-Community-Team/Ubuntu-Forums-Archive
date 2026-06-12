---
title: "Users $HOME/.dmrc file is being ingnored"
date: 2009-02-12
forum: General Help
---

### Post by Grukmuck on 2009-02-12
i get this message whenever i boot up.

Users $HOME/.dmrc file is being ignored.This prevents the default sessions and language from being saved. File should be owned by the user and have 644 permissions. Users $HOME directory must be owned by user and not wirtable by other users.

last thing i remember doing was messing around with conky and trying to get it the way i want. i think i shut down to go to school or work, and when i booted up next, i got that message and get it every time i boot.

what exactly does that mean, and how do i fix it?


thanks

-gruk

---

### Post by mttman on 2009-02-12
Hello,

I think that it means your home directory has had the permissions changed on it. you can try this ```
sudo chmod 644 ~/.dmrc 
``` this wouldn't do much if it didn't work (aka fairly safe) 
or you could ```
 sudo chmod 700 ~ 
``` (potentially bad)
I just want to say one thing before you do - this second one could seriously break your installation or not, i don't know, i'm guessing with that one.

also try this thread : [http://ubuntuforums.org/showthread.php?t=1001307&highlight=Users+%24HOME%2F.dmrc+file+ingnored]("http://ubuntuforums.org/showthread.php?t=1001307&highlight=Users+%24HOME%2F.dmrc+file+ingnored")
this thread says it's solved

Hope this helps

<Mttman>

---

### Post by steveneddy on 2009-02-12
Here is the answer:

change every instance of steve1 to your user name

```
sudo chmod 644 /home/steve1/.dmrc
sudo chown steve1 /home/steve1/.dmrc
sudo chmod -R 700 /home/steve1
sudo chown -R steve1 /home/steve1
```

---

### Post by Grukmuck on 2009-02-12
cool it worked. thanks alot!

-gruk

---

### Post by steveneddy on 2009-02-19
> **Grukmuck said:**
> cool it worked. thanks alot!

-gruk

You are welcome.

---

### Post by glotz on 2009-02-19
I've also seen this thing happen, twice actually. Why do we see it, what's changing those permissions?

---

### Post by mcduck on 2009-02-19
> **glotz said:**
> I've also seen this thing happen, twice actually. Why do we see it, what's changing those permissions?

Usually it's a result from running graphical applications using "sudo" instead of "gksudo". "sudo" doesn't set root's environment variables correctly for graphical applications (as it's intended for command-line use only) so it means you are running programs as root, but with normal user's environment. For some programs this is not a problem, but for others it results in user's configurtion files getting overwritten as root.

Using "sudo -s" or "sudo su" might also result in user's files becoming owned by root. To start a root session in command line you should use "sudo -i", it's pretty much same thing as with sudo VS gksudo. You'll even see the difference easily, running "sudo -i" will move you to root's home directory, just like if you had logged in as root.

---

### Post by glotz on 2009-02-19
Ah, sounds like a credible explanation, thanks!

---

