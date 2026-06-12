---
title: "How to use Thunderbird 1.5rc2?"
date: 2006-01-12
forum: General Help
---

### Post by mario.rimann on 2006-01-12
Hi all!
I'm new to Ubuntu and linux in general. I got used to WinXP and there was using Mozilla Thunderbird 1.5rc2 without any problems.

Now I tried to get the newest rc to run on Ubuntu 5.10 Breezy. I downloaded the compressed file from the Mozilla FTP. Then unpacked it to the Desktop.

This is the point where I ran into problems: What's next? The release Information just tells me to double-click on the executable to start the program. So I tried to double-click "thunderbird" - but nothing happens. No programm starting, no HDD activity like when starting a program, and: NO error messages.

Has anyone a hint into the right direction for me? Google didn't help me.

Hope there's someone that can help me!

Greetings from Switzerland,
Mario

---

### Post by kaamos on 2006-01-12
Open a terminal and navigate to the thunderbird folder (with something like "cd Desktop/thunderbird") and type ./thunderbird and post here what it does.

BTW: Thunderbird 1.5 is released so you might want to install that.

---

### Post by mario.rimann on 2006-01-12
Hi kaamos

That's what I didn't know: enter ./ in front of the file to start it. And you are right, there was the following error shown:

./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

So I installed the missing Library using Synaptic and then it worked! Thanks for your fast answer!

BTW: Thunderbird 1.5 wasn't out this morning when I tried it :-) It's cool that it's out now!

---

