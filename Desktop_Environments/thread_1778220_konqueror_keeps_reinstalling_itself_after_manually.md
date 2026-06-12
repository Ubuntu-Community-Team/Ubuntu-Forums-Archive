---
title: "konqueror keeps reinstalling itself after manually removing over and over again"
date: 2011-06-08
forum: Desktop Environments
---

### Post by 13east on 2011-06-08
I don't need nor like konqueror. I have tried removing it in multiple ways on multiple occasions: through Ubuntu Software Center, KPackageKit, and Terminal (sudo aptitude purge konqueror). But this package keeps reinstalling itself thorough system updates.  

Is there any way to blacklist this program so as it doesn't keeps reinstalling itself through needed system updates?

---

### Post by cornflake000 on 2011-06-09
It could be half installed which means there are some left over references to konqueror in dpkg.

try this first:

sudo dpkg --force-depends --remove konqueror

If that doesn't work then you might need to remove some files manually.

try this next:

Go to the directory /var/lib/dpkg/info/ and remove all references to konqueror.  In a terminal, you can go to that directory and "sudo rm konqueror*" and removed all the files that refer to konqueror.

Afterward, you may need to "sudo apt-get remove -f konqueror".

I hope this helps.

---

### Post by 13east on 2011-06-09
> **cornflake000 said:**
> It could be half installed which means there are some left over references to konqueror in dpkg.

try this first:

sudo dpkg --force-depends --remove konqueror

If that doesn't work then you might need to remove some files manually.

try this next:

Go to the directory /var/lib/dpkg/info/ and remove all references to konqueror.  In a terminal, you can go to that directory and "sudo rm konqueror*" and removed all the files that refer to konqueror.

Afterward, you may need to "sudo apt-get remove -f konqueror".

I hope this helps.

Tried your suggestions; each step returned output saying that there's nothing there.  Only time will tell if it gets installed again.

Thx for you help.

---

### Post by cornflake000 on 2011-06-09
That's weird.  I had the same thing happen to me on one of my servers recently.  This program just kept on installing itself.  In my case though, the install failed each time.  This was the only thing that fixed it.

Sorry...

---

### Post by 13east on 2011-06-09
> **cornflake000 said:**
> That's weird.  I had the same thing happen to me on one of my servers recently.  This program just kept on installing itself.  In my case though, the install failed each time.  This was the only thing that fixed it.

Sorry...

It's not a failed installation; Konqueror runs properly (at least on the first click to launch the program).

no worries... I can just run the terminal command to get rid of it until I find a better solution... 

Thx for your input.

---

