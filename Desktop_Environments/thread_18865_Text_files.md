---
title: "Text files"
date: 2005-03-09
forum: Desktop Environments
---

### Post by Ron W on 2005-03-09
How do I save text files written in gedit to read the same in Windows? Windows prints the 'return' as a box and does not place the text following it onto the next line.

Thanks

Ron

---

### Post by Juergen on 2005-03-09
Only Notepad is that dumb :-) Even Wordpad can display unix-texts correctly AFAIK.

To convert textfiles in Linux you can add these to your .bashrc:
```
alias unix2dos='recode lat1:ibmpc'
alias dos2unix='recode ibmpc:lat1'
```and use the appropriate one or use 'recode' directly (time to waste? Type 'info recode' ;-)).

---

### Post by Ron W on 2005-03-15
Thanks for your reply Juergen.

I want to know more about recode before I add it. Unfortunately, I've not been able to find any information on my system. I've tried the following:-

	1) 'info recode', 
		not give any information
	2) 'man info', 
		gives 'no manual entry for recode'
	3) 'recode --help'
		bash: recode: command not found

Do you know what's going wrong?

I'm a bit of a beginner with Ubuntu, Linux, and bash - hence the reason for probably a simple question.

Thanks

Ron

---

### Post by eternity on 2005-03-15
Run:
sudo apt-get install recode

---

