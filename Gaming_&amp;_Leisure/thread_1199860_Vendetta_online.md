---
title: "Vendetta online"
date: 2009-06-29
forum: Gaming &amp; Leisure
---

### Post by damdempsel on 2009-06-29
I downloaded Vendetta Online and then did what it asked me to type in terminal to install it. After that it said that it was installing and it finished. I went to the folder where it saved the executable and I double clicked it. After that nothing happened. There weren't any other files in the folder other then that. I looked back at the terminal to see where it saved the game files. It said that they were in the same spot as the executable. So how do I get the installation to work?

---

### Post by Dedoimedo on 2009-06-29
If you installed, then it should be in the path, try typing vendetta on the command line, then hit tab to complete.

See this as well:

[http://gwos.org/doku.php/guides:64bit:vendetta_online](http://gwos.org/doku.php/guides:64bit:vendetta_online)

[http://gwos.org/doku.php/guides:32bit:vendetta_online](http://gwos.org/doku.php/guides:32bit:vendetta_online)


Cheers,
Dedoimedo

---

### Post by damdempsel on 2009-06-29
I followed the instructions on the page you gave me and when I tried to open it, it said "Failed to execute child process "/home/damdempsel/.vendetta/update.rlb" (Permission denied)"

Any ideas?

---

### Post by Dedoimedo on 2009-06-29
Check the permissions with ls -ld <relevant-dir> or <file>.
If you're not the owner, then (sudo) chown you:your-group <target>.

To change all files and directories recursively:

(sudo) chown you:your-group <target-dir>/* -R

Regards,
Dedoimedo

---

### Post by Sukotto on 2009-08-07
I installed Vendetta and am haveing a few problems with it. First the game resolution is bigger then my screen and can be annoying, plus the game keep locking up and sound skipping for 30 -40 sec at a time.

---

### Post by Bölvaður on 2009-08-07
> **Sukotto said:**
> I installed Vendetta and am haveing a few problems with it. First the game resolution is bigger then my screen and can be annoying, plus the game keep locking up and sound skipping for 30 -40 sec at a time.

This is unrelated to the OP's problem even though it is the same game, so you should have made a new thread for this topic.


I might be able to help you with the resolution though.
Open Nautilus (file manager) and browse to  your home directory (/home/Sukotto/) and press ctrl+H to see the hidden directories that keep config files.

Look for something similar to .vandetta (all the hidden folders begin with a dot)
in there should be a config file where you can change the resolution I would assume.

---

