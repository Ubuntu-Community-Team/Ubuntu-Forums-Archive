---
title: "How can I install packages without internet connection?"
date: 2006-04-19
forum: Desktop Environments
---

### Post by ec2 on 2006-04-19
I don't have an internet connection. (This isn't the problem)
And I need to install new programs (like multimedia codecs and other stuff), but i havent't found a way to install them without Synaptic package Manager. And Synaptic doesn't let me install packages that i have already downloaded from http//packages.ubuntu.com. I have tried to combine "sudo apt-get install" and the filesystem address of the package (like /home/celer/desktop/packages/lame.deb). but nothing works. If there is someone out there, who knows how to install packages (Debian, .DEB) without accessing the internet, then PLEASE tell me...

---

### Post by sYs^ on 2006-04-19
sudo dpkg -i /home/celer/desktop/packages/lame.deb

---

### Post by ec2 on 2006-04-19
I Think I already tried that, it made a fev errors in the terminal, and that was that.... Isn't there a more sure way? (That will work for sure?)

---

### Post by sYs^ on 2006-04-19
This one should work, what was the output?

---

### Post by ec2 on 2006-04-19
Ok. I'll try that. Thanks... :)

---

