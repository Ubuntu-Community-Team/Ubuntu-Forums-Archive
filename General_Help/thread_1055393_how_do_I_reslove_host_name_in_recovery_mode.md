---
title: "how do I reslove host name in recovery mode?"
date: 2009-01-30
forum: General Help
---

### Post by ozguitarplayer on 2009-01-30
Hi,
look I know there are a lot of really good posts about re: changing host names in recovery mode i.e. /etc/hosts however I don't know how to do that in recovery mode, everything just flashes past and stops at a set of choices that seem to have nothing to do with host names, I'm new to this so I know I'm missing something but what is it...

..or is there a way to change the host name without going into recovery mode, the problem is that I keek getting this message in terminal 
sudo: unable to resolve host Master

all help appreciated

---

### Post by slakkie on 2009-01-30
You have sudo problems.. Then you need to drop to single user mode. If you have a root password set, you can use su to drop to root and change either the sudoers file or the hostfile. 

For the sudoers file you need to set !fqdn as one of the Defaults: [http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options](http://www.gratisoft.us/sudo/man/sudoers.html#sudoers_options)

If you changed your hostname, make sure the hostname is in your hosts file:

127.0.0.1 mynewhostname

or change your hostname once again via the hostname command. 

But you will need root to do any of these changes.. And due to the problem you have right now, single user mode is the answer..

---

### Post by ozguitarplayer on 2009-01-30
thanks slakkie, however I'm such a beginner that I understood little of that,,,I can't recall changeing my host name..too cautious of creating these sort of issues...

how do I drop to single user mode?

and when I use su I get the following..
nigel@Master:~$ su
Password:
su: Authentication failure
nigel@Master:~$

---

### Post by slakkie on 2009-01-30
It is called recovery mode in grub iirc. reboot your machine, when the grub loader appears enter it, then select recovery mode or single user mode, depending on which one is present. Then you should be able to go into single user mode.

---

### Post by ozguitarplayer on 2009-01-30
thanks for your patience, when th egrub screen appears I do get a recovery mode option but not single user mode, when I select recovery mode it all just flashes by so fast I don't know what's happening...

---

### Post by slakkie on 2009-01-30
That is not much information to work with. Give me a minute. I'll try to make some screenshots for you so I can explain what I want you to do.

---

### Post by ozguitarplayer on 2009-01-30
thanks...going out for a couple of hours..will look forward to the screen shots..

---

### Post by avtolle on 2009-01-30
Good thought, slakkie. 

@ozguitarplayer, one of the choices that you should have once in Recovery Mode is something akin to "Drop into a root terminal". I'll let slakkie get his screenshots up so you can see what to do, but this is where you need to be to take care of the host name issue. Good luck to you.

---

### Post by slakkie on 2009-01-30
It is from a 6.10 install, and a server install, but it shouldn't be that different:


Look for this:
[http://opperschaap.net/~wesleys/grub_choose.png](http://opperschaap.net/~wesleys/grub_choose.png)

Select the highlighted option:
[http://opperschaap.net/~wesleys/grub_mode.png](http://opperschaap.net/~wesleys/grub_mode.png)

Your kernel version will be different, no doubt, and probably the selection box will be blue, but it should be the same.

Then you would open an editor and edit your hosts file:

nano /etc/hosts and edit the 127.0.1.1, or change the hostname back to the original hostname in /etc/hostname.

Once you are done, save the changes, and type exit (or reboot) and your machine should boot normally and you should be able to use sudo again.

---

### Post by slakkie on 2009-01-30
> **avtolle said:**
> Good thought, slakkie. 


tbh, i had this problem once myself. On Ubuntu 5.04 or 5.10 I changed my hostname via the hostname command and I couldn't use sudo anymore... It was a bit anoying (from that moment onwards I always set the root password so I don't need to drop to single user mode to solve issues like these anymore :)).

---

### Post by ozguitarplayer on 2009-01-30
thanks heaps again,
at the risk of making myself look foolish, I should mention that I have a seperate HHD with windows and I use startup manager...hope I shouldn't have mentioned this before...

grub displays;
ubuntu 8.10, kernel 2.6.27-11 generic
ubuntu 8.10, kernel 2.6.27-11 generic recovery mode
ubuntu 8.10, kernel 2.6.27-9 generic
ubuntu 8.10, kernel 2.6.27-9 generic recovery mode
ubuntu 8.10, kernel 2.6.27-7 generic
ubuntu 8.10, kernel 2.6.27-7 generic recovery mode 
as well as ...memtest..
and...windows
I only mention this list of ubunyu in case it has any bearing

anyway thanks for the screen shots and info however when I select recovery mode I am unable to see how to open a editor....would this be because I'm using startup manager?

---

### Post by slakkie on 2009-01-30
You are using this: [http://startupmanager.org/](http://startupmanager.org/)??

That should not bite with Ubuntu.. I think.

You should select the second option of grub btw: ubuntu 8.10, kernel 2.6.27-11 generic recovery mode

---

### Post by ozguitarplayer on 2009-01-30
It's the only startup manager I could find in synaptic it's a KDE startup manager 2.24.0

many times I have tried the second option and when I press enter it all flashes past very quick until it stops on the screen with a number of options with 
Drop into root terminal being one of them, is this where is change the settings, or do I not press enter on the second option and use the 'e' or 'c'
keys to change things...I have looked at these with no result....

thanks again for your patience..

---

### Post by slakkie on 2009-01-30
> **ozguitarplayer said:**
> It's the only startup manager I could find in synaptic it's a KDE startup manager 2.24.0

many times I have tried the second option and when I press enter it all flashes past very quick until it stops on the screen with a number of options with 
Drop into root terminal being one of them, is this where is change the settings, or do I not press enter on the second option and use the 'e' or 'c'
keys to change things...I have looked at these with no result....

thanks again for your patience..

Select the root terminal option, this should give you a root prompt. Then do the following:

cat /etc/hosts

look for an entry like 127.0.1.1 foo foo.localdomain etc etc

Now do the following:

hostname foo

This will set the hostname to foo

Or the other way around is also possible:

run hostname (without options), this will show you for example bar.

Now use an editor to edit the hosts file (nano in this example):
nano /etc/hosts and change all the foo entries to bar.

If we take the previous example:

127.0.1.1 foo foo.localdomain
becomes
127.0.1.1 bar bar.localdomain

While we are here, edit your sudoers file to make sure you can use sudo so we never have to do this again.

visudo 

You should see a line somewhere at the top with Defaults, add !fqdn to that line eg

Defaults    !lecture,tty_tickets

becomes

Defaults    !lecture,tty_tickets,!fqdn

Save the file and type either exit or reboot (exit will continue booting to your normal bootlevel).

---

### Post by ozguitarplayer on 2009-01-31
ok..done, many thanks slakkie, the level of support form this forum is great

---

### Post by slakkie on 2009-01-31
np man, glad i could help.

---

