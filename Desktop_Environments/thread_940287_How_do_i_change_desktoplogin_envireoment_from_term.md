---
title: "How do i change desktop/login envireoment from terminal?"
date: 2008-10-06
forum: Desktop Environments
---

### Post by MasterNetra on 2008-10-06
How do i change desktop/login envireoment from terminal? I recently removed KDE4 and i wasn't even promopted to change the login enviroment or whatever and i want it back to gnome.

---

### Post by overdrank on 2008-10-06
> **MasterNetra said:**
> How do i change desktop/login envireoment from terminal? I recently removed KDE4 and i wasn't even promopted to change the login enviroment or whatever and i want it back to gnome.

Hi and you should be able to restart x with the ctrl, alt, backspace keys and then change the session at the login.

---

### Post by MasterNetra on 2008-10-06
Doesn't work. I'm not in a GUI enviroment at login now nor when i login. Its all command prompt. I need to change the stuff from thinking it needs to be KDE4 to Gnome.

---

### Post by MasterNetra on 2008-10-07
Let me rephrase this... How do you change out of KDE4 stuff from the terminal/Command Prompt? 
Sense KDE4 style was used at login. Seeing as KDE4 removed without the system putting in a replace ment it defaults to a command prompt login thing. Although after logging in your still stuck at command prompt..

---

### Post by MasterNetra on 2008-10-07
*Bump* Unresolved

---

### Post by maruthi_s@infosys.com on 2008-10-07
[COLOR="Blue"]
Not sure whether I understood your question clearly, But you can change the login by using su -u or dong a ssh to the environment you wish to login with a different user id. 
[/COLOR]

---

### Post by snowpine on 2008-10-07
Can you run 'gdm' to get back to the graphical login?

---

### Post by MasterNetra on 2008-10-07
How do i run gdm from command prompt? And to maruthi. I am asking how to change the Xserver login from using KDE4 (which is uninstalled) back to use gnome so that i can graphically login and use my accounts in a GUI again. Esstentially is what i'm asking.

---

### Post by tspan on 2008-10-07
I think that this should work:

```

sudo dpkg-reconfigure gdm

```

then reboot.

If not, then:

Check if /etc/X11/default-display-manager file consists only of "/usr/sbin/gdm" without quotes. 

```

cat /etc/X11/default-display-manager

```

If not, edit /etc/X11/default-display-manager and write only /usr/sbin/gdm 

```

sudo nano /etc/X11/default-display-manager

```

Ctrl-O to save, Ctrl-X to exit nano.

Then run:

```

sudo update-rc.d gdm defaults

```

If gdm, GNOME, etc. are all installed properly you should just run:

```

sudo /etc/init.d/gdm start

```

to start gdm and X or you could just reboot your machine.

Hope this helped.

---

### Post by MasterNetra on 2008-10-07
That first option worked thanks a bunch!

> **tspan said:**
> I think that this should work:

```

sudo dpkg-reconfigure gdm

```

then reboot.

If not, then:

Check if /etc/X11/default-display-manager file consists only of "/usr/sbin/gdm" without quotes. 

```

cat /etc/X11/default-display-manager

```

If not, edit /etc/X11/default-display-manager and write only /usr/sbin/gdm 

```

sudo nano /etc/X11/default-display-manager

```

Ctrl-O to save, Ctrl-X to exit nano.

Then run:

```

sudo update-rc.d gdm defaults

```

If gdm, GNOME, etc. are all installed properly you should just run:

```

sudo /etc/init.d/gdm start

```

to start gdm and X or you could just reboot your machine.

Hope this helped.

---

