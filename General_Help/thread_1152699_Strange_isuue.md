---
title: "Strange isuue"
date: 2009-05-08
forum: General Help
---

### Post by kewl_123 on 2009-05-08
Hi,
     I am quite new to using Ubuntu so dont know if this is OK.
I have downloaded some podcasts as MP3 and saved it in a folder. When I open that folder and take the cursor on any file, the file starts playing automatically. No music player is opened but I hear the sound of that clip being played.
The only thing I have done is download something when I used it the first time to enable it to play MP3 and all. I remember it said something with the word 'ugly' in it while describing the downloads. I downloaded it as it said something about it being supported by Ubuntu community.
Is it OK or some security issue?
Thank you.

( Can someone please tell me how to find out until when will  the version of Ubuntu I am using be supported?)

---

### Post by Yellow Pasque on 2009-05-08
If you hover your cursor over a media file, Nautilus will start playing it. This is not a security issue. You can change this behavior with Edit -> Preferences -> Preview tab.

"Ugly" probably refers to the gstreamer-plugins-ugly package, which contains the codecs necessary to play mp3.

---

### Post by kewl_123 on 2009-05-08
> **Temüjin said:**
> 
"Ugly" probably refers to the gstreamer-plugins-ugly package, which contains the codecs necessary to play mp3.

So I take it as I didnt download any malware.
Thank you.

---

### Post by MysticalRiotCandy on 2009-05-08
It's actually a really nifty feature of Nautilus.  It also shows you what your images look like, so you don't have to actually open them up in your image application.  I believe that it also shows lines of text files as well.

---

### Post by The-ITu on 2009-05-08
> **kewl_123 said:**
> So I take it as I didnt download any malware.
Thank you.
creating a virus for Linux is virtually impossible. 
any virus made for Linux **must** be user exacted so be smart about what you type into the terminal.

---

### Post by kewl_123 on 2009-05-08
> **The-ITu said:**
> any virus made for Linux **must** be user exacted so be smart about what you type into the terminal.

Can you please elaborate or direct to some article abt it?
From what I have read abt security, the only concern seems to be downloading from good repositories. But I dont know which ones to avoid yet.

---

### Post by MysticalRiotCandy on 2009-05-08
> **The-ITu said:**
> creating a virus for Linux is virtually impossible. 
any virus made for Linux **must** be user exacted so be smart about what you type into the terminal.
I wouldn't go as far to say it's impossible, but it's not nearly as easy as it is to create a simple batch virus for a Windows machine to format C:\.  For a virus to work, it'd have to be able to modify system files, whether the reason is to add in a logger or to just delete files therein.  What Unix (base of Linux) does is it creates two accounts immediately on the install.  There is the primary user account, which is your account.  Then there's the root account.  This is the account that can modify anything and everything in your filesystem.  In Windows, the default account to be logged into is already at administrator-level.  Any virus that hits the Joe Window's PC is able to modify all the files.  However, in Unix, because of the permissions separation, there is an added difficulty.  Because you need to sudo in order to do anything nearly risque, that already hampers down a virus' objective.  'Sudo' will always prompt you for a password when you run the command.  As such, Unix itself will not allow the executable to run unless it gives the system the password that allows it to do so.  That's why you should pick a strong password for root account, and why you should never, ever log into root account, for any purpose.  Use sudo when you need to.

---

### Post by kewl_123 on 2009-05-08
So unless I myself have started some action that asks for root password...I should never type it.

---

