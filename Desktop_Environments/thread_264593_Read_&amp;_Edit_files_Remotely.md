---
title: "Read &amp; Edit files Remotely"
date: 2006-09-24
forum: Desktop Environments
---

### Post by misteral on 2006-09-24
I've found lots of threads about controlling PC's remotely.. I'm interested in only reading/editing files.

My wife is in school and wants to be able to edit her files on our home Ubuntu box from school. She has access to both Windows and Mac hardware.

I know I can get ssh running, log in or use sftp, make it all nice with a dynamic dns utility, but for the Mrs., something that's point & click, or as close as possible, would be ideal.

I looked at BarracudaDrive - it looks closest, but unless I'm missing something you can't edit a live document (i.e. save it on the remote box, not on the local one). Also, even though I told it to look at one certain folder, it gave up access on my entire PC.

Typically, she'll be accessing documents through Microsoft or Open Office (so, word/ODT documents)

I thought if I could find some (easy) remote viewer like GoToMyPC or something (preferably free) that would be OK, but all this space seems to be going to windows. I'd prefer to use something that has 0 footprint - autodownload on access of a website/something is OK, but having to download VNC and VNC into the box is not.

Can anyone recomend anything or am I aiming too high?
Thanks!

---

### Post by kidders on 2006-09-24
Hi there,

For Linux/Mac/Windows compatibility, Samba filesharing is your best bet. Of course, it would be ludicrous to leave Windows filesharing ports open on your computer, and far too much bother to set up a VPN, so (if it were me) I'd tunnel Samba over SSH. The result would be a secure (but slightly slow) point-and-click interface :-)

---

### Post by misteral on 2006-09-25
Thanks for your suggestion! Sounds like that should do it, I've been working to get Samba set up just for around the house, once I get that going I'll try to get it tunnelling.
Thanks!

---

### Post by stilus on 2006-09-25
You might want to look into ifolder as well. I havent set it up myself yet, but it seems to provide almost transparent filesynchronisation. It's not exactly "on the fly remote editing", but there are clients for linux, windows and I believe Mac. 

Mind you, this is only hear-say, so everybody please feel free to correct me if I'm wrong. 

kind regards,
stilus

---

### Post by misteral on 2006-09-25
stilus  
I checked out iFolder. It looks very promissing, but since it needs a client to work it won't fit the bill. 

Mapping a network drive should be perfect. I've managed to get SSH working, forwarding through my router. Now to tackle Samba.

---

### Post by kidders on 2006-09-26
Hi misteral,

Since you seem to be going that route, you'll notice that there's a bit of a trick to getting Windows to cooperate with tunnelled shares. There are some perfectly good HOWTOs around to get you started though. Basically, you'll need to set up a redundant loopback interface on the client and bind your Samba server to it by forwarding the ports there.

If you use puTTY (or a similar SSH client that can remember some connection settings), with key-based encryption, your users can set up the port forwarding simply by double-clicking an icon. From there, it's business as usual to access the shares.

Edit: The Mac-based setup is similar ... well, one of the ways of doing it on a Mac is.

---

### Post by misteral on 2006-09-26
kidders
I've seen several howto's, but none involving clicking an icon. Would you have any URL's you can point me to?
Thx

---

### Post by kidders on 2006-09-26
Not off the top of my head, but I can try to explain what I was thinking about ...

The first time you try to access your files remotely, it would be a case of trial and error. Once you were sure you had things just the way you wanted them, you could arrange something like this:

[LIST=1]
[*]Install puTTY on a Windows box.
[*]Log into your fileserver.
[*]Generate yourself a public/private key pair.
[*]SCP the private key to your Windows box and tell puTTY about it.
[*]Set up a loopback network interface at, say, 10.0.0.1.
[*]Create & save a puTTY connection profile that forwards local (ie local to the Unix box) port 139, etc. to 10.0.0.1.
[*]Read about puTTY's command line options.
[*]Create a .lnk file on your user's desktop that opens puTTY and invokes your saved connection profile.
[/LIST]

Now, your users could set up the (nasty and complex) port forwarding mess simply by double-clicking the puTTY shortcut, providing access to remote files in the normal way, by running "\\10.0.0.1\sharename", for example. Thanks to the key setup (step 3), they wouldn't even need to give puTTY a password.

That's roughly what I had in mind, but as you can see, _you_ would have to set it up first, as the average Windoze user won't know how.

Just in case, it might be worth reminding you that, depending on the speed of your Ubuntu box's internet connection, the SSH encryption might make your fileshares a little sluggish. The pay-off is that your users would access remote data in a way that's familiar to them, avoiding any fuss & confusion.

Let me know if you think the idea is any good. Your alternative would be to teach your users to use an SCP/FTP/WebDAV client, perhaps.

---

### Post by misteral on 2006-09-26
Here's what I have so far.

Samba: Working perfectly inside my home network. W2K laptop connects, maps network drive, I'm half way to happy.

My next step is to get connected from OUTSIDE my home network. Before I go opening ports on my router, I wanted to make sure I understood it all.

When I go to connect from my remote PC, I need to basically execute ssh thusly (I'll be running this through cygwin, if not I'll set up a tunnel through PuTTY):

ssh -L 139:localhost:139 my.home.pc

Here's where I'm not sure what to do next.](*,) 

Everything I've read so far says that since it will now map port 139 to my tunnel, ALL windows file sharing will now be disabled? Or will it only be for the file share to this one machine?

I've also seen instructions for changing the HOSTS file on the Windows PC, is this really necessary?  This will be done from Windows XP boxes, if it makes any difference. If it comes easier on a Mac I can ask the Mrs. to use the macs at her school instead of the MS PC's.

Thanks everyone for your help so far!

---

### Post by kidders on 2006-09-27
I *think* I follow what you're getting at. The "simpleton" way to make non-local fileshares locally accessible via SSH is to forward ports to 127.0.0.1, which necessitates disabling any programs that might already be using the port.

This is the reason for setting up a redundant loopback network interface (see my previous post). That way, local filesharing can be left switched on. (The "smart" way hehe.)

I hope that answers your question.

---

