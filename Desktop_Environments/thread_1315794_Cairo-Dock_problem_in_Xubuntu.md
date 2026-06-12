---
title: "Cairo-Dock problem in Xubuntu"
date: 2009-11-05
forum: Desktop Environments
---

### Post by kestrel1 on 2009-11-05
Just started using Xubuntu 9.10 on an older machine. In general I really like Xubuntu, but there is a small problem with Cairo-Dock. If I start Cairo-Dock it works fine, but on restart I get a message about using the openGL version or not. I shutdown the dock & added it to the startup applications with ```
cairo-dock -c
```
This works fine for the first restart, but after that I get two docks running & I still get the openGL message.
I do not want to use the openGL version, but cannot find a way to stop this message or opening of the two docks unless I remove one from the startup apps list.
Hope this makes sense. Been using Ubuntu for a long time, but the xfce desktop is a bit different to gnome.

---

### Post by fabounet on 2009-11-06
maybe XFCE records the opening applications when you logout, and restart them when you log in.
hence the double dock.

---

### Post by kestrel1 on 2009-11-06
> **fabounet said:**
> maybe XFCE records the opening applications when you logout, and restart them when you log in.
hence the double dock.
Yes that was my guess, but how can I stop it doing this? It is getting annoying. This morning I started up & I had three docks start up, but I noticed that another was in the start up apps list, so I removed it. I don't know how it got there because I never put it there.
I like the XFCE interface, but need to find out a bit more about it. I am used to gnome, but surely it is not that different.
Thanks for any help.

---

### Post by Mark76 on 2009-11-06
You need to disable recall previous session, iirc.

---

### Post by kestrel1 on 2009-11-06
> **Mark76 said:**
> You need to disable recall previous session, iirc.
How? I have looked Session & Startup, but cannot see anything about recall previous session.

---

### Post by Mark76 on 2009-11-06
I'll tell you later when I switch DEs.

---

### Post by kestrel1 on 2009-11-06
> **Mark76 said:**
> I'll tell you later when I switch DEs.
I just looked again in Sessions & Startup & the option is there to automatically save the session at logout, but this is not actually ticked.
I deleted the sessions with ```
rm -rf ~/.cache/sessions
``` & then restarted. Cairo-Dock didn't start as I thought. So I added Cairo-dock to the start up apps list, logged out & cairo-dock started. Logged out again & Cairo-Dock started twice, once giving me the opengl message. I have now removed it from the startup list & it still starts with the opengl message, although it should not as the Auto save session is not ticked.
This is weird.

UPDATE:
I thought I would have a look in the ~/.cache/sessions folder. I found the sessions file & it has cairo-dock down as a:```
Legacy0_Command=cairo-dock
```
I edited this so that it read:```
Legacy0_Command=cairo-dock -c
```
as I thought this would sort it, but on logging out & back in again I still got the opengl message. I checked the file & it had reverted back to the original without the modification.
I had a look at the bak file of the same name & this has held my modification. I redid it just to make sure that I was not a complete fool & edited the wrong file, but this did exactly the same. So for some reason it is saving the sessions, even though it has been told not to.
Any ideas.
Cheers

---

### Post by kestrel1 on 2009-11-06
Anyone with an idea?

---

### Post by Mark76 on 2009-11-06
Sorry, that was my idea :o

---

### Post by kestrel1 on 2009-11-06
> **Mark76 said:**
> Sorry, that was my idea :o
Cheers, I will have to dig around a bit then & see if I can find out what is going on :-)

---

### Post by wmartyr on 2009-11-21
Hi guys.

I'm using archlinux + xfce but this might work in xubuntu as well.

I went to /home/user/.cache/sessions/xfce4-session-archhost:0. Note that "archhost" might be "localhost" on your computer or some other word. I deleted lines:

Legacy0_Screen=0
Legacy0_Command=cairo-dock
Legacy0_ClientMachine=archhost
LegacyCount=1

Near the end of the file. Open Menu-Settings-Session and Startup. Uncheck "Automatically save session on logout". Then go to "Application Autostart Tab" and make sure that you have an entry in for Cairo-Dock to start, with -o or -c options. Then when you logout, uncheck the "Save Session for future logins" box.

Worked for me.

---

### Post by kestrel1 on 2009-11-23
> **wmartyr said:**
> Hi guys.

I'm using archlinux + xfce but this might work in xubuntu as well.

I went to /home/user/.cache/sessions/xfce4-session-archhost:0. Note that "archhost" might be "localhost" on your computer or some other word. I deleted lines:

Legacy0_Screen=0
Legacy0_Command=cairo-dock
Legacy0_ClientMachine=archhost
LegacyCount=1

Near the end of the file. Open Menu-Settings-Session and Startup. Uncheck "Automatically save session on logout". Then go to "Application Autostart Tab" and make sure that you have an entry in for Cairo-Dock to start, with -o or -c options. Then when you logout, uncheck the "Save Session for future logins" box.

Worked for me.

This is essentially what I had been doing, but I now removed the rest of the legacy stuff etc. It should not be saving the session at logout & I set Cairo-dock to start automatically. This works fine for the first start up after doing the changes, but if I logout & back in again I have two cairo-docks running & the legacy entry is back in the sessions file. I also get the message about starting cairo-dock with OpenGL etc.
So it looks like it is saving the session at logout even though it has been told not to.

---

### Post by kestrel1 on 2009-11-26
I have now solved this one & I feel a right fool. On the logout/shutdown menu box there is a tick box that says 'Save Session for future logins' This was ticked. therefore the session was being saved. I removed the tick & logged in again, but just had to re-do the sessions file so that the legacy lines had been removed. I enabled Cairo-Dock to start automatically & it is now working correctly.
Such a simple thing that I overlooked. :oops:

---

### Post by aspiredfang on 2009-12-14
I am facing a similar issue to what has been been discussed in this thread. However, I like to save my sessions on logging out. Please forgive me for being a *nix noob and asking outright how to make the following script work, I have had a look around the net and just seem to be missing something very fundamental to its running. 

Coming from a background in PHP, I would normally run the 'ps...' command in the selection statement itself but, bash cried about it being improper syntax? Here's what I have in mind and can come up with, help with the actual syntax would be appreciated. As it stands, Cairo-dock will always launch another instance :(

- Make variable $check a list of any running processes matching the literal 'cairo-dock -c'
- perform check on variable to see if it is empty
- If empty run command 'cairo-dock -c'

```

#Cairo-start.sh 
$check = ps aux | grep 'cairo-dock -c';  
if [$check = '']  then
   cairo-dock -c 
fi  

```Kudos and thanks in advance for any response :)

---

