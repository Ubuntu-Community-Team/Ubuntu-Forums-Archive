---
title: "Forum email is gibberish?"
date: 2005-05-12
forum: Forum Feedback &amp; Help
---

### Post by Bob D. on 2005-05-12
I get an email notification of activity in a thread I posted into. I just started getting the emails with the text all as gibberish. Sample of the text below:

 > SGVsbG8gQm9iIEQuLAoKZm5nIGhhcyBqdXN0IHJlcGxpZWQgdG8gYSB0aHJlYWQgeW91IGhhdmUg

c3Vic2NyaWJlZCB0byBlbnRpdGxlZCAtIFdoYXQgYXJlIHlvdSBsaXN0ZW5pbmcgdG8gcmlnaHQg

bm93PyAtIGluIHRoZSBDb21tdW5pdHkgQ2hhdCBmb3J1bSBvZiBVYnVudHUgRm9ydW1zLgoKVGhp

cyB0aHJlYWQgaXMgbG9jYXRlZCBhdDoKaHR0cDovL3VidW50dWZvcnVtcy5vcmcvc2hvd3RocmVh

ZC5waHA/dD0zMjI3OCZnb3RvPW5ld3Bvc3QKCkhlcmUgaXMgdGhlIG1lc3NhZ2UgdGhhdCBoYXMg

anVzdCBiZWVuIHBvc3RlZDoKKioqKioqKioqKioqKioqCm5pZ2h0d2lzaCAtIHdpc2htYXN0ZXIK

Ym95IHNldHMgZmlyZSAtIHJvb2tpZQoqKioqKioqKioqKioqKioKCgpUaGVyZSBtYXkgYmUgb3Ro

ZXIgcmVwbGllcyBhbHNvLCBidXQgeW91IHdpbGwgbm90IHJlY2VpdmUgYW55IG1vcmUgbm90aWZp

Y2F0aW9ucyB1bnRpbCB5b3UgdmlzaXQgdGhlIGZvcnVtIGFnYWluLgoKWW91cnMsClVidW50dSBG

b3J1bXMgdGVhbQoKfn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fgpVbnN1YnNj

cmlwdGlvbiBpbmZvcm1hdGlvbjoKClRvIHVuc3Vic2NyaWJlIGZyb20gdGhpcyB0aHJlYWQsIHBs

ZWFzZSB2aXNpdCB0aGlzIHBhZ2U6Cmh0dHA6Ly91YnVudHVmb3J1bXMub3JnL3N1YnNjcmlwdGlv

bi5waHA/ZG89dXN1YiZ0PTMyMjc4CgpUbyB1bnN1YnNjcmliZSBmcm9tIEFMTCB0aHJlYWRzLCBw

bGVhc2UgdmlzaXQgdGhpcyBwYWdlOgpodHRwOi8vdWJ1bnR1Zm9ydW1zLm9yZy9zdWJzY3JpcHRp

b24ucGhwP2RvPXZpZXdzdWJzY3JpcHRpb24mZm9sZGVyaWQ9YWxs  
This only seems to happen with emails from UbuntuForums. Email I get from others is fine. I sent an email to myself from my main email account to me through my Gmail account (my UbuntuForums mail comes through my Gmail account). I can receive and read that email from Gmail just fine.

This appears to be a site issue? Anyone else seeing this?

Bob

p.s. my email client is Evolution if that matters.

---

### Post by qstone on 2005-05-12
[QUOTE=Bob D.]
Anyone else seeing this?
[/QUOTE]

I do  :) 
I use Evolution (2.0.2, yes I'm still on Warty), too.

Anyone knows where it might come from ?

---

### Post by Bob D. on 2005-05-12
Must be a glitch in the forum software. The header seems fine since I'm getting the email. It's just the body text of the email that is hosed.

Well, hopefully ubuntu-geek will see thses posts and take a look. Glad to know it's not just me. Thanks qstone!

Bob

---

### Post by ubuntu-geek on 2005-05-12
I'll take a look at it later on tonight. So this happens when you subscribe to a thread and then the email you receive it the garbled one?

---

### Post by Bob D. on 2005-05-12
[QUOTE=ubuntu-geek]I'll take a look at it later on tonight. So this happens when you subscribe to a thread and then the email you receive it the garbled one?[/QUOTE]
 Exactly.

Don't know if this helps, but here is a bit of the header from a readable email received May 11:

  ```
 To: xxxxxxxx@gmail.com
 Subject: Reply to post 'What are you listening to right now?'
 From: "Ubuntu Forums Forums" <site@ubuntuforums.org>
 Message-ID: <200505120107.2466ca956116@ubuntuforums.org>
 X-Priority: 3
 X-Mailer: vBulletin Mail via PHP
 MIME-Version: 1.0
 Content-Type: text/plain; charset="ISO-8859-1"
 Content-Transfer-Encoding: 8bit
 Date: Wed, 11 May 2005 21:21:07 -0400 (EDT)
```   

and this is what I'm seeing in emails from the forum software today (May 12, diff in bold):

  ```
To: xxxxxxxx@gmail.com
Subject: Reply to post 'Forum email is gibberish?'
From: "Ubuntu Forums Forums" <site@ubuntuforums.org>
Message-ID: <200505122021.9261bb345355@www.ubuntuforums.org>
X-Priority: 3
X-Mailer: vBulletin Mail via PHP
MIME-Version: 1.0
Content-Type: text/plain; charset="ISO-8859-1"
[b] Mime-Version: 1.0
 X-Invalid-Content-Type: text/plain; charset=UTF-8
 Content-Transfer-Encoding: BASE64
[/b] Date: Thu, 12 May 2005 16:40:22 -0400 (EDT)
```

That seems to be the only change in the header I can see. Perhaps that is the issue?

Bob

---

### Post by TravisNewman on 2005-05-12
Woop. Lookie there. Same thing happening with me now. Didn't start until just a few minutes ago though, strange.

---

### Post by Gandalf on 2005-05-12
same thing happened to me, all today mails are like this
```

SGVsbG8gR2FuZGFsZiwKClJlaGV2a29yIGhhcyBqdXN0IHJlcGxpZWQgdG8gYSB0aHJlYWQgeW91
IGhhdmUgc3Vic2NyaWJlZCB0byBlbnRpdGxlZCAtIEhPV1RPOiBIZWFyIG11bHRpcGxlIHNvdW5k
cyB1c2luZyBCb3RoIEVTRCAmIEFMU0EgLSBpbiB0aGUgSG9hcnkgNS4wNCBDdXN0b21pemF0aW9u
IFRpcHMgJiBUcmlja3MgZm9ydW0gb2YgVWJ1bnR1IEZvcnVtcy4KClRoaXMgdGhyZWFkIGlzIGxv
Y2F0ZWQgYXQ6Cmh0dHA6Ly91YnVudHVmb3J1bXMub3JnL3Nob3d0aHJlYWQucGhwP3Q9MzIwNjMm
Z290bz1uZXdwb3N0CgpIZXJlIGlzIHRoZSBtZXNzYWdlIHRoYXQgaGFzIGp1c3QgYmVlbiBwb3N0
ZWQ6CioqKioqKioqKioqKioqKgpXZWxsLCBJIGRpZCB0aGF0LCBidXQgaXQgd291bGQganVzdCBw
bGF5IGEgc2VyaWVzIG9mIHBjIHNwZWFrZXIgYmVlcHMgYW5kIHRoZSBpbnRlcmZhY2Ugc291bmRz
IGluIFVidW50dSBzdGlsbCB3b3VsZG4ndCBwbGF5LiBJdCB3b3VsZCBvbmx5IHdvcmsgaWYgSSBy
ZWJvb3RlZC4KCkZvcnR1bmF0ZWx5LCBJIGRvbid0IGhhdmUgdG8gd29ycnkgYWJvdXQgdGhhdCBu
b3cgOikKKioqKioqKioqKioqKioqCgoKVGhlcmUgbWF5IGJlIG90aGVyIHJlcGxpZXMgYWxzbywg
YnV0IHlvdSB3aWxsIG5vdCByZWNlaXZlIGFueSBtb3JlIG5vdGlmaWNhdGlvbnMgdW50aWwgeW91
IHZpc2l0IHRoZSBmb3J1bSBhZ2Fpbi4KCllvdXJzLApVYnVudHUgRm9ydW1zIHRlYW0KCn5+fn5+
fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn5+fn4KVW5zdWJzY3JpcHRpb24gaW5mb3JtYXRp
b246CgpUbyB1bnN1YnNjcmliZSBmcm9tIHRoaXMgdGhyZWFkLCBwbGVhc2UgdmlzaXQgdGhpcyBw
YWdlOgpodHRwOi8vdWJ1bnR1Zm9ydW1zLm9yZy9zdWJzY3JpcHRpb24ucGhwP2RvPXVzdWImdD0z
MjA2MwoKVG8gdW5zdWJzY3JpYmUgZnJvbSBBTEwgdGhyZWFkcywgcGxlYXNlIHZpc2l0IHRoaXMg
cGFnZToKaHR0cDovL3VidW50dWZvcnVtcy5vcmcvc3Vic2NyaXB0aW9uLnBocD9kbz12aWV3c3Vi
c2NyaXB0aW9uJmZvbGRlcmlkPWFsbA==
.

```

i thought it was a problem in my config...

---

### Post by ubuntu-geek on 2005-05-13
Should be fixed now :) Let me know if it isnt.

---

### Post by Gandalf on 2005-05-13
[QUOTE=ubuntu-geek]Should be fixed now :) Let me know if it isnt.[/QUOTE]
 yep exactly, i received this one :D
thanks master

---

### Post by TravisNewman on 2005-05-13
hoorah!

---

