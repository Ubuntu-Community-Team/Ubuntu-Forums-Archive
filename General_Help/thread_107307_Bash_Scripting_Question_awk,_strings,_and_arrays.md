---
title: "Bash Scripting Question: awk, strings, and arrays"
date: 2005-12-22
forum: General Help
---

### Post by tidalwav1 on 2005-12-22
Hi, people,

Basically, I'm working with a string in this format:

Subject: text Subject: more text Subject: even more text

I want to populate an array (in a bash shell script) with data from the string, whose eventual elements, when working from the above example, would look like this:

text
more text
even more text

I'm guessing it's possible to use awk to do this, but I have no idea how...can anyone point me in the right direction?

---

### Post by darth_vector on 2005-12-22
sorry, havent used awk. you could do it in sed by replacing the ":" with "\n" like this:

sed 's/:/\n/g' filename

---

### Post by tidalwav1 on 2005-12-22
I don't follow.

Would 'filename' be the a containing the string? If so, what you suggested doesn't work, but I'm not sure I follow.

---

### Post by darth_vector on 2005-12-22
yes, filename contains the string. i forgot to remove the "Subject". try this one:

sed 's/Subject:/\n/g' filename

if by "doesnt work" you meant that the command failed, then you probably dont have sed installed, cause it works fine for me.

so if you want an array you would do something like:

for i in `sed 's/Subject:/\n/g' filename`; do
...

---

### Post by tidalwav1 on 2005-12-22
Okay, makes more sense. Seems to be working, too--thanks! :)

---

