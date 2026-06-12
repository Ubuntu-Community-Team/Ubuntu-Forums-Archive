---
title: "[Ubuntu 12.04 LTS] Problems installing Vega Strike"
date: 2014-08-19
forum: Gaming &amp; Leisure
---

### Post by TheCommissar on 2014-08-19
So I've been attempting to install Vega Strike for a wee while. I downloaded the tarball from the sourcefourge page, and extracted it successfully. Attempting to run "install.sh" in the terminal, however, causes a terminal window to flash up for a second, then disappear with no effects. I'm not sure what is going on here. The command in the terminal to run "install.sh" results in an "unable to open" message.

I've checked the permissions on the file and it looks like I have the obvious (allow executing file to run as a program) ticked. Google-fu has produced no useful results.

What am I missing, and is there an alternative route to installing what looks like rather a good game?

Cheers in advance.

---

### Post by oldrocker99 on 2014-08-19
Are you using dotslash, i.e. ```
./command
```

That's one way to run, the other is
```
[sudo]sh command
```
You use sudo if you want the program installed in a root directory, otherwise it'll stay in your home folder.

Have you tried both?

---

### Post by TheCommissar on 2014-08-19
Yep, just tried both. I get this:

```
sh: 0: Can't open ./install.sh
```

Or this:

```
sh: 0: Can't open install.sh
```

Depending on whether I use dotslash or sudo.

---

