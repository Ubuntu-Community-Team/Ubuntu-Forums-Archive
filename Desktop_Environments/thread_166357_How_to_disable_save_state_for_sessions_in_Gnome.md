---
title: "How to disable save state for sessions in Gnome?"
date: 2006-04-26
forum: Desktop Environments
---

### Post by d00d on 2006-04-26
I am using Gnome 2.12.1 on Ubuntu 5.10 I want to know how one can disable the state save-across-session feature for some applications that seem to support it. Specifically the problem relates to Firestarter firewall, whose state is saved across the sessions. Whenever I login it complains about admin rights which my normal user doesn't have. However I already have enabled Firestarter at startup by having editing the sudoers file. In affect Fiestarter starts twice, once due to the saved state and once due to sudo firestarter --start-hidden command.

I didn't use Automatix and had installed Firestarter manually.

I have written the entry in the startup as

sudo firestarter --start-hidden

and there is an entry in my /etc/sudoers file for my user

<username> ALL=NOPASSWD: /usr/sbin/firestarter

So the startup entry doesn't give me any trouble while running firestarter

But due to session save (I think) there is another entry

/usr/sbin/firestarter --sm-config-prefix /firestarter-otDezh/ --sm-client-id 105e3fa07f000114605809900000098260000 --screen 0

which complains about insufficient rights, also I noticed that the command in startup (sudo firestarter --start-hidden) runs as root but the command when state of session is restored is run as the non previliged user

PS I had posted this question at linuxquestions.org but didn't get a solution that'd work :(

---

### Post by louis_nichols on 2006-04-26
I know this isn't in any way an answer to your question, but the thing is you really don't need to start firestarter at logon. Firestarter just creates rules for iptables, which are automatically loaded at startup (not logon) and work irrespective of wether the GUI is started or not.

The GUI is needed only when you need to add/modify/remove rules.

---

### Post by d00d on 2006-04-28
Yes I know that it runs as a service, however I need to load the GUI to see all the open connections, transfer rate etc.

---

### Post by louis_nichols on 2006-04-28
Well... I can see yo took your instructions directly from fs's online documentation, so it should work. Here's what I recommend: open the session manager and, in the list with currently running apps for current session, select all firestarter entries and click **remove**, then **apply**. You should just have the one under startup programs.

Then, things should be better at next logon, I think.

---

### Post by d00d on 2006-04-29
Thanks for the reply.

Yes I have already done the step you suggested, but it does not work.

Here's what I think happens

When I remove the entry /usr/sbin/firestarter --sm-config-prefix /firestarter-otDezh/ --sm-client-id 105e3fa07f000114605809900000098260000 --screen 0 , this entry is already a temporary entry valid for only that session so it makes no difference. However the sudo firestarter --start-hidden command creates a new running instance of firestarter which on logging out, is saved as a 'state' and on the next logon, another entry (different from the one created and deleted earlier) is made. So the removal of the entry from the startup list becomes futile.

Another solution that I can think of (apart from disabling the sae-session for firestarter) is that I write a script to execute at log-off that will shut off the GUI and therefore the state of the firewall won't be saved. If this can be a solution, I would request someone if they could tell me how to create a script that would run at the end of a Gnome session at logoff.

---

