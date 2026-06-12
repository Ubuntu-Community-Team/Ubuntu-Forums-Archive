---
title: "Thanks Ubuntu"
date: 2008-05-09
forum: Desktop Environments
---

### Post by Superevil on 2008-05-09
Yesterday I was moving all my pictures from my /pictures folder onto my external hard drive pictures folder and it just so happened I had a jpg file (which ubuntu didn't have the .jpg extension attached) with the exact same name as a directory in the main pictures folder on the external HD and as I was moving the files I was typing something and the skip/replace dialog popped up for a split second so now I've lost that entire folder with irreplaceable pictures because I guess Ubuntu can't tell the difference between a file without an extension and a directory of the same name. Oh and having the REPLACE button selected by default? Stupid idea. I've had no other complaints with Ubuntu other than now.

---

### Post by tdrusk on 2008-05-09
> **Superevil said:**
> Yesterday I was moving all my pictures from my /pictures folder onto my external hard drive pictures folder and it just so happened I had a jpg file (which ubuntu didn't have the .jpg extension attached) with the exact same name as a directory in the main pictures folder on the external HD and as I was moving the files I was typing something and the skip/replace dialog popped up for a split second so now I've lost that entire folder with irreplaceable pictures because I guess Ubuntu can't tell the difference between a file without an extension and a directory of the same name. Oh and having the REPLACE button selected by default? Stupid idea. I've had no other complaints with Ubuntu other than now.

You are complaining about a mistake you made. 

I think mac and windows both make replace the default.

---

### Post by Zorael on 2008-05-09
Wow, damn. I'd demand a refund if I were you.

---

### Post by tacutu on 2008-05-09
no, he has a good point. If you're typing and just pressing "enter" when the dialog pops up, the keyboard event (i.e. the "enter" key) will be received -- accidentaly -- by the dialog window. 

I feel for you, Superevil, what happened is really nasty.

---

### Post by Zorael on 2008-05-09
And this is not the standard for other operating systems, as well? Keystrokes will traditionally be sent to whichever window has focus, and in the case of popups, them getting focus and being on top of everything is sort of their point.

I'm sorry for the loss of your data, but "Thanks Ubuntu" is projecting.

---

### Post by tacutu on 2008-05-09
if feature X is the default for OSX or Win, it doesn't mean that it is inherently a good feature. Linux doesn't necessarily have to be like the rest. It can be better, you know!

personally, i prefer the dialog windows not to capture focus and jump on top of all other windows but rather notify me in the taskbar area (some programs do this, some don't)

---

### Post by Zorael on 2008-05-09
> **tacutu said:**
> if feature X is the default for OSX or Win, it doesn't mean that it is inherently a good feature. Linux doesn't necessarily have to be like the rest. It can be better, you know!
This is, of course, true. Ideas can be posted on [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu), as suggestions.

---

### Post by tacutu on 2008-05-09
perhaps this could be taken to gnome developers, as it is a larger UI design issue.

Re: your sig, can I get a kookie?

---

### Post by Superevil on 2008-05-09
> **tdrusk said:**
> You are complaining about a mistake you made. 

I think mac and windows both make replace the default.

I didn't blame the loss of my data on the OS smart guy. My main complaint is when you're gonna have a Skip/Replace dialog maybe its a better idea to have SKIP selected by default instead on REPLACE.

---

### Post by kellemes on 2008-05-09
> **Superevil said:**
> I didn't blame the loss of my data on the OS smart guy. My main complaint is when you're gonna have a Skip/Replace dialog maybe its a better idea to have SKIP selected by default instead on REPLACE.

Good point indeed, I agree totally.
Still.. the title is rather suggestive I guess..

---

### Post by tszanon on 2008-05-09
Create backup copies often, and hope you never need them.

---

### Post by prshah on 2008-05-09
> **Superevil said:**
> I've lost that entire folder with irreplaceable pictures because I guess Ubuntu can't tell the difference between a file without an extension and a directory of the same name.

Getting back to the topic at hand; if indeed the directory has been replaced, then the files exist, just the entry point is lost. Reboot into recovery mode, run fsck, then check under the /lost+found directory.. are your irreplaceable pictures there?

EDIT: I just tried to reproduce what OP did, and I have to agree with him; this behavior is not correct. He _should_ file a bug report. Though the wording of the dialog is very clear, in this case, replace should _not_ be the default choice. On my next reboot, I will try an fsck to see if the files can be recovered.

---

### Post by Therion on 2008-05-09
A little too late for a Ctrl+Z at this point, I'm guessing...

---

### Post by gottabeandrew on 2008-05-09
It happens to me in ubuntu and windows. I hate it. I'm typing something on msn, i press the space bar or enter key and just as i press it, something pops up and is gone before i can see what it was.

---

