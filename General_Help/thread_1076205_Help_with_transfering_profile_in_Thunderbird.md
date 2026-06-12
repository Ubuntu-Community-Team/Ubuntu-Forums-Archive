---
title: "Help with transfering profile in Thunderbird"
date: 2009-02-21
forum: General Help
---

### Post by sittingnev on 2009-02-21
Hi guys,
Just installed ubuntu and am sorting out my e-mail.
I'm using thunderbird and want to transfer the settings from when I was using it in windoze. 
I have the profiles file from that on a cd. I'm just wondering how to do it here.

Thanks in advance
Nev

---

### Post by sub2007 on 2009-02-21
Copy the profile folder into ~/.thunderbird (~ is /home/*your username*)

Then enter into a terminal

```
thunderbird --ProfileManager
```

You only need to run it from Terminal that one time unless adding new profiles.

Click "Create Profile", give the profile a name and then click "Choose Folder...". Then you just point it at your profile folder. 

Make sure that "Don't Ask At Startup" is checked (unless multiple users will be using Thunderbird) and start Thunderbird.

Next time you start it you can use your shortcuts to start it and and won't have to use the terminal.

---

### Post by sittingnev on 2009-02-21
cant find /thunderbird, file. (Is this important?)
Copied the profile folder into documents. and pointed profile manager to it, not working.
Anything to do with the fact the folder has come over from windows or, off cd?

---

### Post by sittingnev on 2009-02-21
sorry me being a dunce and pointing profile manager to wrong file #-o 

Thanks for the help, now working fine.

---

