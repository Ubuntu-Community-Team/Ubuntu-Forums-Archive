---
title: "Moving files..."
date: 2009-04-08
forum: General Help
---

### Post by Briandb1222 on 2009-04-08
I tried moving a driver file to its corresponding folder, though since I use Ubuntu, I'm unsure what folder I should put it in. I have an S3 UniChrome Pro Integrated graphics card...and I hope I got the right driver. I found a folder called via_rhine under modules and tried moving it to the driver folder in that folder using sudo. When I used the move command which I got from reading another post, I got a error saying that the file I'm trying to move didn't exist, which it does. Someone help please. Am I putting it in the correct folder? And how do I move it correctly using sudo?

---

### Post by mb_webguy on 2009-04-08
I'm not sure why you're doing anything with driver "files".  In Linux, drivers are either included in the kernel, or added as modules to the kernel.  Once you install it, you're done.  And if you have some kind of driver "file" that isn't a deb or installer of some sort, I don't know *what* you have, but it doesn't sound like a Linux driver to me.

The basic syntax of mv is "mv /path/to/current_location /path/to/new_location".

---

### Post by Briandb1222 on 2009-04-08
I have an S3 Unichrome Pro. Ubuntu apparently doesn't support this kind of driver so I had to download it from viaarena.com. I do not have an ATI or GeForce which Ubuntu supports.

---

### Post by kryptikos on 2009-04-08
I take it you went to: [http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220]("http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220") and none of those are the exact card? That site has Ubuntu drivers available. It has a zip download and when I checked inside it has "installation.txt" which is the instructions on how to install and use the driver. Have you followed that?

---

### Post by Briandb1222 on 2009-04-09
hmmmm no not yet. And, no none of them were the exact cards...I installed a random one and hope to god it works hehe.

---

### Post by Briandb1222 on 2009-04-09
I have went over it and not sure I understood because I typed in the commands of what it told me to do and nothing happened. However, I think the install was built for Linux and not Ubuntu.

---

