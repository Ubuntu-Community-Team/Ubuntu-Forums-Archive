---
title: "Shut down desktop gui and go back to terminal only?"
date: 2008-11-18
forum: Desktop Environments
---

### Post by Nubii on 2008-11-18
Hi Ubuntu forum!

Was just wondering, well i installed ubuntu server yesterday. Threw a ubuntu desktop on it and i all worked as it should.

But is there any way that i can quit the desktop, and return to the "prompt" only? my reason to do this is that i want to save the ressources that the desktop takes use of, and let the server koncentrate on the terminal processes that i'm running. 

Hope that you guys can help me out. 
I installed the desktop to setup my terminal processes, but now that i've set it up, I dont need my server to start the Desktop up at the moment.

Regards Nubii

---

### Post by hictio on 2008-11-18
Yes, there is a way :D
Open a Terminal, and type this:

```

update-rc.d -f gdm remove (ENTER)

```

---

### Post by decoherence on 2008-11-18
Or if you want a more temporary way...

```
sudo /etc/init.d/gdm stop
```

and

```
sudo /etc/init.d/gdm start
```

to start it back up (rebooting will also default back to the GUI)

---

### Post by hictio on 2008-11-18
> **decoherence said:**
> Or if you want a more temporary way...

```
sudo /etc/init.d/gdm stop
```

and

```
sudo /etc/init.d/gdm start
```

to start it back up (rebooting will also default back to the GUI)

Well... "My way" :) is temporary too, you can revert to the GUI by typing:

```

update-rc.d -f gdm defaults (ENTER)

```

Or, if you have shut down the GUI, you are logged at the CLI, and want a full blown desktop, simply type:

```

startx (ENTER)

```

When you logout of the, say, Gnome session, you are back the CLI.

---

### Post by binbash on 2008-11-18
start the server at init 3

---

### Post by wylfing on 2008-11-18
Nubii - It depends on what you want to accomplish. hictio's method is the "right" way to make this kind of configuration change, but it will result in never seeing Gnome again until you re-enable it. decoherence's method will result in Gnome re-appearing whenever you reboot (and then you'll have to manually stop gdm again).

---

