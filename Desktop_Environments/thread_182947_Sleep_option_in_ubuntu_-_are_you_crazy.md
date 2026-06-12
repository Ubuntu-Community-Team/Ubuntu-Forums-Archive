---
title: "Sleep option in ubuntu - are you crazy?"
date: 2006-05-27
forum: Desktop Environments
---

### Post by Richard Roy on 2006-05-27
What's wrong with you?
I've been trying form one month to fix the sleep option. Then, I find this thread, and fixed it:
to enable suspend (or hibernate), you have to enable it in the gnome-power-manager conf:
- Run gconf-editor.
- Go in apps/gnome-power-manager
- Enable "Can suspend" or/and "Can hibernate"
Now it should work. If it's not, you could check acpi-support to know if suspend and/or hibernate is enable.
- sudo gedit /etc/default/acpi-support
- Uncomment ACPI_SLEEP=true to enable suspend
- Uncomment ACPI_HIBERNATE=true to enable hibernate

How the hell should I have guessed it?
What's wrong with ubuntu developers? It's a great OS, realy ! So why make life so hard????

---

### Post by ashrack on 2006-05-27
[QUOTE=Richard Roy]What's wrong with you?
I've been trying form one month to fix the sleep option. Then, I find this thread, and fixed it:
to enable suspend (or hibernate), you have to enable it in the gnome-power-manager conf:
- Run gconf-editor.
- Go in apps/gnome-power-manager
- Enable "Can suspend" or/and "Can hibernate"
Now it should work. If it's not, you could check acpi-support to know if suspend and/or hibernate is enable.
- sudo gedit /etc/default/acpi-support
- Uncomment ACPI_SLEEP=true to enable suspend
- Uncomment ACPI_HIBERNATE=true to enable hibernate

How the hell should I have guessed it?
What's wrong with ubuntu developers? It's a great OS, realy ! So why make life so hard????[/QUOTE]
I believe that this is because the UBUNTU evaluates your computer and if UBUNTU things its good for suspend than it automaticly enables this function. 
On my computer I have all of them options always enabled but suspend doesnt work. So its a prety flawed detection IMHO

---

### Post by kiddo on 2006-05-27
Maybe because they felt the  feature was not mature enough, just a guess. And finding this in gconf took me about 20 seconds, personnally. It's not like you had to recompile anything.

---

### Post by ssam on 2006-05-27
if you file a bug, saying that your machine can sleep fine when these options are enabled, then the devs can probably whitelist you machine.

---

### Post by missmoondog on 2006-05-31
hmm? just found this thread and everything is already set correctly. suspend locks the box up tight as a drum, when being restored. :(

does this on all 3 dapper boxes i have.

---

### Post by bruce89 on 2006-05-31
I did suspend once, it broke, but then Ubuntu disabled the option.

---

### Post by mannheim on 2006-05-31
You don't need to use gconf-editor to change this setting. You can change it with Preferences-->Power Management.

If it is not already enabled, go to "Power Management" and select the "General" tab. For the chosen "action" when inactive or when the sleep button is pressed, select "Suspend". If the gconf option "can_suspend" is presently not checked, then you'll get a warning dialog, saying that suspend may not work. If you go ahead anyway, then the Power Management preferences app will change the "can_suspend" gconf setting silently, and you are all set.

So there is no really "hidden" option here. The real issues are whether suspend actually works: on my desktop machine, it has never worked with Ubuntu (though Windows XP has managed).

---

### Post by ruffneck on 2006-05-31
[QUOTE=missmoondog]hmm? just found this thread and everything is already set correctly. suspend locks the box up tight as a drum, when being restored. :(

does this on all 3 dapper boxes i have.[/QUOTE]

Try logging out first --> Options ---> Suspend. Then resume it after a couple of seconds. See if this works for you.

---

### Post by seanUSXIII on 2006-05-31
I noticed with dapper beta 2 that I can suspend and for a while its fine. If I wait more than a few hours to start back up though, it hangs. Anyone else notice this?

---

### Post by l.tambiah on 2006-06-07
Not 100% sure but the I think the reason there are hibernate suspend issues is due to the kernel not having suspend2 included. This decision was took to not overbloat the kernel with unneccessary code. I believe there is a new project (which is not production ready) which runs the acpi from the user space. 

[http://suspend.sourceforge.net/]("http://suspend.sourceforge.net/")

---

