---
title: "GproFTPd/ProFTPd:  I can connect remotely, but no directory listing...  ??"
date: 2006-07-20
forum: Desktop Environments
---

### Post by n00buntu NJ on 2006-07-20
I have installed ProFTPd and GproFTPd which are working beautifully behind my router.  

I can even log in remotely, I've done it from a Windows XP machine via FileZilla and from the command prompt.  

I can watch these connections from the GproFTPd "Transfers" screen, and see that the connection is being made, but...  On the client side everything seems to be working until it times out while trying to populate the directory.

](*,) 

?  Any ideas  ?


EDIT:  Sorry, forgot to mention that I'm running 6.06...

---

### Post by Thund3rstruck on 2006-07-21
The same thing happened to me as well. You need to force gFTP to switch off passive mode (I can't remember the place its set). Once you turn off passive mode, it will get forwarded through the router to the right machine and your directory listing will then appear

---

### Post by mrbaz on 2006-07-21
I have the same exact problem.  Nothing I do seems to remedy it.

---

### Post by JohanSwe on 2006-07-22
> **Thund3rstruck said:**
> The same thing happened to me as well. You need to force gFTP to switch off passive mode (I can't remember the place its set). Once you turn off passive mode, it will get forwarded through the router to the right machine and your directory listing will then appear

What is passive mode? I'm mounting ftp servers in nautilus and there is no such setting.

I can mount and open the server. But it's just empty. 

Someone who has got GproFTPd up running in Ubuntu Dapper?

---

### Post by JohanSwe on 2006-07-22
Now I got it up running. I edited the user and the group for the server to root and changed the permissions for the ftp folder in /home/. Later on I will try to change this for better security. Any tips?

But I can only see the files and the folders if I connect from Ubuntu, not from a ftp client in windows. Please take a look at my screenshot.

---

### Post by n00buntu NJ on 2006-07-22
I don't know if we are all having the same problem.  I have GproFTPd working as it should from my house.  I can use any computer, yes even Windows, to connect to my FTP server from behind my router.  

Outside my router, which I've only been able to test from 2 windows machines, I can connect, but no directory listing.

I doubt that changing a setting in gFTP will do anything for GproFTPd/ProFTPd, since it is just a client.  

Any other ideas?

---

### Post by JohanSwe on 2006-07-22
> **n00buntu NJ said:**
> 
I doubt that changing a setting in gFTP will do anything for GproFTPd/ProFTPd, since it is just a client.  

Why are you mentioning gFTP when you're having problem when connecting from windows computers?

---

### Post by Thund3rstruck on 2006-07-22
I mis-read the question. I have had an issue where my linux clients could not get a directory listing from the FTP server based on the fact that gFTP is defaulted to use passive mode. 

--

---

### Post by JohanSwe on 2006-07-22
I can access my server from windows but the log file says it is by anonymous access. Please see my previous attachment. I'm trying to log in with user name and password so I can't understand this.

But what actually is passive mode and anonymous access?

---

### Post by n00buntu NJ on 2006-07-22
> **JohanSwe said:**
> Why are you mentioning gFTP when you're having problem when connecting from windows computers?

Because this suggestion was given...

> **Thund3rstruck said:**
> The same thing happened to me as well. You need to force gFTP to switch off passive mode (I can't remember the place its set). Once you turn off passive mode, it will get forwarded through the router to the right machine and your directory listing will then appear

And I thought the same thing as you - it has nothing to do with my problem.  

I guess I'll just have to figure it out on my own...

---

### Post by JohanSwe on 2006-07-22
It works for me now. The problem was settings in the windows client. Using a nother client should it should work without changing anything in that client.

n00buntu NJ: I guess your problem is the router. Have you set up port forwarding?

---

### Post by n00buntu NJ on 2006-07-29
> **JohanSwe said:**
> It works for me now. The problem was settings in the windows client. Using a nother client should it should work without changing anything in that client.

n00buntu NJ: I guess your problem is the router. Have you set up port forwarding?

Yes, I have forwarded the port to access FTP and I can login to the server from a remote location (e.g. my work).  

If I login from a command line terminal, I can enter my user/pass and get the welcome message.  After that I'll send a 'ls' or 'dir' command, which always times out.  

I think that I need to forward the passive ports, but I can't seem to figure out how to forward a range of port numbers on my router.

---

### Post by shorys on 2006-10-24
For me worked like this:

The client (FTP Client plugin from Service Salamnder file manager) set in active mode.
For each folder in proftpd.conf add:

<Limit EPSV PASV>
   DenyAll
</Limit>

---

