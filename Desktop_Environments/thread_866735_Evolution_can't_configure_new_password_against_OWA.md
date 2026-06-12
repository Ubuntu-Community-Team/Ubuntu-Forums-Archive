---
title: "Evolution: can't configure new password against OWA"
date: 2008-07-22
forum: Desktop Environments
---

### Post by airflow on 2008-07-22
Hi,

I'm using Evolution for some time now in my company against the Exchange-server there. It always worked, but since I changed my password today I can't seem to configure the new password in Evolution, too! :(

Evolution asks me for the new password, I enter it, but I'm immediately asked again - although it's definitely the right one.

When I start Evolution from the console, I see the following error-messages when trying to authenticate:

```
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'

```

Anyone knows what does that mean and how to fix it?

regards,
airflow

---

### Post by airflow on 2008-07-24
Help! :( I still couldn't fix this highly annoying problem...

What I have tried:

* Deleting my keyring, and letting ubuntu create a new one (named "login"). 
* Deleting and recreating my email-account in evolution.

Didn't really change anything. Except I see a new error-log-message from evolution:

```
** (evolution:7556): WARNING **: couldn't connect to daemon at $GNOME_KEYRING_SOCKET: /tmp/keyring-Hl5izR/socket: Connection refused
```

Any hints highly appreciated!
airflow

---

### Post by louferd on 2008-08-07
Any luck fixing this?  I've had the same problem and evolution is now completely useless.  Before Hardy, I had no problems with it, but it's been one critical error after another since the upgrade. Terrible.  It should never have been released like this.

---

### Post by airflow on 2008-08-15
I invested significant time in recovering this problem, as basically my daily work flow depends heavily on being able in responding to email. I tried to recreate a new evolution-configuration by reconfiguring everything in the options several times, and all of a sudden it worked again - but for me the process wasn't consistent - i have tried the same things before without luck. Sorry to not being able to give you a reproducible solution.

regards,
airflow

---

### Post by dlstyley on 2008-08-31
I think something is wrong with the GUI interface where you enter your exchange settings.  I logged the following bug... have no idea where that will go.  

[https://bugs.launchpad.net/bugs/262348](https://bugs.launchpad.net/bugs/262348)

The key is to start Evolution with debugging turned on for the Exchange connector (E2K_DEBUG=5).  Then you can see what is being passed to the OWA server and debug from there.  I had to manually edit the configuration instead of using the GUI.

---

### Post by firsttry on 2008-09-01
I have the same problem:

```
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have key 'exchange:xxxxxxx;auth_Basic@XX.X.X.XXX_'
evolution-shell-Message: Killing old version of evolution-data-server...

```

It's really annoying as I use evolution at work and I have loads of filters set up - I tried moving the whole ~/.evolution folder somewhere else to get evo to regenerate it, but no luck there either. Hope someone has a fix for this!

---

### Post by dlstyley on 2008-09-02
Did you try turning on debugging to see what is being sent to the exchange server?  

What I found is that the configuration settings weren't being stored properly, so it was sending a request to the server that looked like this:

http://my.server.com/Exchange/username/username

Editing the settings directly in gconf-editor and removing the extra username in the URL fixed it for me.

---

### Post by krivine on 2008-09-02
> **dlstyley said:**
> Did you try turning on debugging to see what is being sent to the exchange server?  

What I found is that the configuration settings weren't being stored properly, so it was sending a request to the server that looked like this:

[http://my.server.com/Exchange/username/username](http://my.server.com/Exchange/username/username)

Editing the settings directly in gconf-editor and removing the extra username in the URL fixed it for me.

I'm a complete newbie; can you give me a pointer to the file that I would need to examine/edit?

Thanks

---

### Post by dlstyley on 2008-09-02
This may be a bit like the blind leading the blind.  ;)

At the command line run:

```
gconf-editor
```

It will open something similar to the registry editor in Windows (if you are familiar with that).  Navigate to /apps/evolution/mail.  In there is a key called "accounts".  when you try to edit it, you won't be able to read it (at least I couldn't). Instead I copied that text into a text editor so I could see the entire string.  I fixed up the connection string and pasted it back in.  

I don't recall for sure, but I think I removed my username from the "owa_path".  May have removed a slash as well.  

So I changed something like this:

> owa_path=/exchange/username/

to something like this:

> owa_path=/exchange

Don't forget to start evolution with debugging from the command-line to see if you can tell what your problem is.  That's how I figured this out.

```
E2K_DEBUG=1 evolution
```

You can use 1-5 as debugging levels to give you more or less detail (5 is most).

---

### Post by krivine on 2008-09-03
He he, at the moment I'll take guidance from anybody who's walked the path before. 

It doesn't immediately solve my problem, but you've given me some more things to look at; thank you.

---

### Post by dlstyley on 2008-09-03
Are you getting any errors showing up in the debug output?  Basically, responses from the HTTP server that aren't in the 2xx range.

---

### Post by krivine on 2008-09-04
Thanks; I ought to confess that my problem has to do with Evolution not remembering passwords for Google diaries - related perhaps, but not the same. I googled the error message, and when I saw your post I was interested to see what you'd done. Your reply really was helpful, and useful: I learnt about gconf and E2K_DEBUG, so once again, thanks. 

The Google calendar problem is a known bug, and I guess I can live with it.

---

### Post by dragonfyre13 on 2008-10-23
MUCH easier way.

```
Edit -> Preferences

Select your exchange account, and hit the edit button on the side.

Change to the Receiving Email tab, and remove your "Mailbox" entry. (Just delete it completely).

Click the Authenticate button, and type in your password when requested. It will refill in your "Mailbox" entry.

Restart Evolution.
```


Just do the above. It will auto fix the config file to have only one mailbox.

---

### Post by lunatico on 2008-11-28
This solution will not work for me as I have not configured my account before. Is there a file where I can go and manually configure this? Could someone give it to me, or give me the string values I should put into gconf-editor?
Thanks!

---

