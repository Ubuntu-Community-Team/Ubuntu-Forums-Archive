---
title: "Find and Replace from the command line"
date: 2006-09-06
forum: Desktop Environments
---

### Post by enopepsoo on 2006-09-06
Hello, All,

I am trying to do a find and replace from the command line (preferably with regexes too).

I have read some documentation for awk, but I found it to be quite confusing.  Does anyone have advice on how to do this?

Thanks!


:KS 
:KS

---

### Post by lagagnon on 2006-09-06
If you are just finding and replacing stuff in text files then sed is what you want (the stream editor). However, awk is much better for doing that with columnar data in text files. For instance to find and replace Tom with Jerry (all instances) in the file "test.txt" you would:

sed -e 's/Tom/Jerry/' test.txt

It's that simple. There are many sed tutorials on the Internet. "man sed" is also very useful. Have fun. sed is VERY powerful once you learn it.

---

### Post by enopepsoo on 2006-09-06
Thanks, Iaganon, I will give that a go!:KS

---

### Post by tminuszero on 2006-09-06
Well, that's a pretty weighty question! You're trying to find certain files and replace text inside those files? awk is certainly one solution. I don't use it too often because, like you, I haven't put the time into it. :)

However, you can do what you need to with just about any scripting language. So if you're more comfortable with perl, php, ruby or python, you can use those.

For instance, I've used this a few times:

perl -pi -e "s/text to find/text to replace/g" *.txt

It looks in every file with a .txt extension in the current folder, and replaces "text to find" with "text to replace" 

You can change it to do whatever you need to do - add recursion, regexp's or whatever. I'm sure the awk version is similar.

**This is *very* simplistic, and it can be dangerous ro your install, so use at your own risk.**

---

### Post by tminuszero on 2006-09-06
Thanks, lagagnon! That's what I was supposed to be using all this time :/

---

