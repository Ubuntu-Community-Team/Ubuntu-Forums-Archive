---
title: "Starting a GUI app via SSH"
date: 2009-03-25
forum: General Help
---

### Post by flamer on 2009-03-25
Is there a command that can start a GUI via SSH? I wanna start my music player on my host with my cellphone (using the cellphone as a sort of a remote control) to start an app. for example Amarok so it can play on a host. Just typing Amarok in terminal gives out an error: cannot connect to X server.

Thank you for your help.

---

### Post by kanikilu on 2009-03-25
I have no idea if this will work from your cell phone (probably not since there needs to be a local X server running), but generally you use: ```
ssh -X user@host
``` assuming X11 forwarding is allowed from the server.

---

### Post by flamer on 2009-03-25
Using the above command there is no output. I think you've misunderstood me. I meant that I want to start from my cellphone Amarok remotely on my server so it will play music on my server not on the cellphone.

---

### Post by kanikilu on 2009-03-25
> **flamer said:**
> Usin the above command there is no output. I think you've misunderstood me. I meant that I want to start from my cellphone Amarok remotely on my server so it will play music on my server not on the cellphone.

Oh I see, yeah I misunderstood. Anyways, yeah, I think there's a way to do that, I haven't tried myself, but try: ```
DISPLAY=:0 amarok
```

---

### Post by mhgsys on 2009-03-25
you mean you got ssh working from your cellphone to your ubuntu?

Sweet, 
anyway. 

I guess there's a better way then mine, but to launch a GUI remotely I always use the export DISPLAY command when logged in true ssh.

meaning, when remotely logged in to the main pc, 
(the 1 you want the GUI on) 

typing in the remote console

```

export DISPLAY=:0

```

then start the GUI

---

### Post by flamer on 2009-03-25
> **kanikilu said:**
> Oh I see, yeah I misunderstood. Anyways, yeah, I think there's a way to do that, I haven't tried myself, but try: ```
DISPLAY=:0 amarok
```

I get an error:

No protocol specified: cannot connect to X server :0

**Mhgsys**,GUI will not work on my cellphone:) It's no biggy really. I have a Symbian OS cellphone and I just installed PortablePUTTY:)

---

### Post by mhgsys on 2009-03-25
> **flamer said:**
> I get an error:

No protocol specified: cannot connect to X server :0

**Mhgsys**,GUI will not work on my cellphone:) It's no biggy really. I have a Symbian OS cellphone and I just installed PortablePUTTY:)


I didn't mean start the gui on your cellphone, 
what I mean is to start a ssh with your PortablePutty, and typ 
```

export DISPLAY=:0

```
on your host with it .

Then start the GUI by typing it's name

edit: about the No protocol specified: cannot connect to X server :0

on your host you have to be logged in to X allready.

---

