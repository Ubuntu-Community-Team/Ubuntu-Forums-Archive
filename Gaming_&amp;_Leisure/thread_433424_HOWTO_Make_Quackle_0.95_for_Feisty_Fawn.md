---
title: "HOWTO: Make Quackle 0.95 for Feisty Fawn"
date: 2007-05-05
forum: Gaming &amp; Leisure
---

### Post by lazyart on 2007-05-05
Quackle is a crossword game simulator.  It implements the rules of Scrabble and is considered the best computer player to date.  After losing a ton of hair trying to make under Dapper and Edgy, I found Feisty is up to snuff.

1. You will need Qt4.2, g++ and SCons to bring everything together:

sudo apt-get install libqt4-dev g++ scons

2. While that is churning, download the Quacle source files from [http://web.mit.edu/jasonkb/www/quackle/#download](http://web.mit.edu/jasonkb/www/quackle/#download) and extract.

3.IMPORTANT: In the extracted directory, look for fixedstring.h and edit it.  Add the line

#include <cassert>

I added it just before the line that reads

namespace Quackle

Save the resulting file and it's time to make quackle. The compile will fail if you omit this step!

4.  Now down to the nitty-gritty.  Go to the terminal and navigate to the directory you extracted the source to.  In my case it was /home/dad/quackle-0.95

cd /home/dad/quackle-0.95
scons r=1

You'll get some messages, hopefully they end on a positive note.

5.  Now at the terminal enter

cd quackleio
qmake
make

You'll get some messages after the last two commands.

6. Now we'll back out and go to another directory and make some more:

cd ..
cd quacker
qmake
make

7. After even more messages you should have a working quackle.

./quacker

---

### Post by adityanag on 2007-06-23
Well, it's working, but why the heck does Quackle not give a default board?

---

### Post by adityanag on 2007-06-23
Ah, I found out. Legal Reasons! Bah.

---

