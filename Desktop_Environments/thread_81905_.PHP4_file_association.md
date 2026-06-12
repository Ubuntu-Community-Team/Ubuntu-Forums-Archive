---
title: ".PHP4 file association"
date: 2005-10-25
forum: Desktop Environments
---

### Post by painjsimpson on 2005-10-25
Hello!

I write my websites in php, and had to change them to .PHP4 due to earthlink.net configs.

Anyway, I FTP'ed in through Konqueror, and associated the .php4 file with Kate (awesome for editing remote files).  I edited my files, and went to see the results.

In Mozilla Firefox 1.0.7, it now prompts to 'Open with: gedit' when I go to load that .php4 file.  It does the same in Konqueror.

For the life of me I cannot dis-associate the extension from gedit, kwrite, and kate.

I am running Breezy Badger, Mozilla 1.0.7, have Kubuntu installed but mainly use GNOME.

I have probably gone into too many wrong places trying to fix this.

Any suggestions on where I make this (what I believe to be) system wide change so I can browse my own sites?!?

Thanks in advance,

Pain J

---

### Post by LorenzoD on 2005-10-25
The "Open with" prompt has nothing to do with the association you've set up. It is because the web server doesn't know what to do with your .PHP4 files. Are you sure you've got the extension right? Shouldn't it maybe be .php4 (lowercase) instead?

---

### Post by painjsimpson on 2005-10-25
Sorry, the title is misleading.  They are lowercase, .php4.  And they worked, off both servers (old one and new one) just fine until I opened it in Kate, and set that association.  

Now, Firefox doesn't work for .php4 (but it does for .php) in KDE or in GNOME, and Konqueror doesn't work.  They just prompt to do something with it defaulting to gedit.

So, it worked before, I made the association, and that was the last of it!

Also, if I open Firefox as root, it has the same problem, so it's not just my user setting, it appears to be system wide.

Thanks!

---

### Post by LorenzoD on 2005-10-25
If I click on a local .php file, it opens with gvim, which I have set to be the default for opening files of type PHP. But this does not affect how epiphany or firefox will treat those files if they are served by a web server (local or remote). If I try to open a PHP file not served by a web server, it will open it with gvim.

---

### Post by elephanthunter on 2005-10-25
The way you say things confuses me (it's probably me, I'm easily confused :p ) So let me verify what you said.

You have a webserver that you ftp your files to. Just recently you associated .php4 files with kate. For some reason you think this affects how Firefox reads .php4 files.

To test this theory, go to [okay.php4](http://www.elephanthunter.us/okay.php4)

[PHP]<?php

	echo 'This .php4 seems to be working okay.';

?>
[/PHP]

If the file opens and displays the text **This .php4 seems to be working okay.** in the browser, then your computer is fine. The problem lays in the remote webserver you are using to host the file.

---

### Post by painjsimpson on 2005-10-26
Results: Webserver is the issue.

I hit the site from another machine, that had worked a few minutes before, and it did the same thing.

Apparently they started to move the DNS records (when they said they hadn't) when they set up their account at xmission (new host), and since I use the xmission dns servers, I was hitting the new site before other machines at my company that use a different DNS server.

If I go to their home public_html it works fine.

Served off the virtual host, it does not.

Thank you for your responses!

Ubuntu rocks!

---

### Post by painjsimpson on 2005-10-26
Yep, xmission updated their configuration, and now it works no problem.

And here I was, feeling all retarded and stuff...

---

