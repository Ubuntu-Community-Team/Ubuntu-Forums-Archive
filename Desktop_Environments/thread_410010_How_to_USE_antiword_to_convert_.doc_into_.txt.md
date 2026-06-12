---
title: "How to USE antiword to convert .doc into .txt"
date: 2007-04-15
forum: Desktop Environments
---

### Post by true_friend on 2007-04-15
Hi folks
I am in a bit problem. want to convert some .doc files into txt. but I canno afford conversion one by one as they are more than 500 . I heard about antiword I installed it but do not know how to work. I want a command by entering whom in main directory( which has .doc files in sub directories) convert all .doc files into .txt of same name at same palaces.
Any ideas?
Regards
True_Friend

---

### Post by kidders on 2007-04-16
Hi there,

What about **[command] *.doc** or **find -name *.doc -exec [command] {} \; **or **for f in *.doc; do [command] $f; done** or something similar?

---

### Post by true_friend on 2007-04-16
first command did not workes it says i cannot read it. third also same result
2nd one gives a speedy unlimited output in terminal but no result in form of txt files.

---

### Post by kidders on 2007-04-16
Could you post what you did and what the results were?

---

### Post by true_friend on 2007-04-17
ss@ss-desktop:~/Desktop/Research Data(All)$ antiword -t *.doc
I can't open '*.doc' for reading
ss@ss-desktop:~/Desktop/Research Data(All)$
--------------------------------------------------------------------------------------------------
2nd's Out put::::::::::::::::::::::::::::
 Sardar Kh a and requested for asylum. Sardar Khan readily
gave him shelter. Alam Khan also arrived after them and Majid Khan made
himself ready for a battle. Meanwhile, his own relatives and friends had
also started from his village to help their master.
A fierce battle raged all the night between the two parties. Umai was
watching all this from the roof top. She feared for Majid and Sardar Khan
because Alam Khan too was a brave warrior. She prayed that Zarif Khan might
arrive soon and the battle be decided in his favour. Early in the morning
the fighters from both sides saw a clo
....................................................
I think it just read the files.
____________________________________________________________
ss@ss-desktop:~/Desktop/Research Data(All)$ 5~for f in *.doc; do antiword -t $f; done
bash: syntax error near unexpected token `do'

---

### Post by kidders on 2007-04-17
Hey again,

> **true_friend said:**
> ss@ss-desktop:~/Desktop/Research Data(All)$ antiword -t *.doc
I can't open '*.doc' for reading
That means there are no word documents in the current directory.

> **true_friend said:**
> ss@ss-desktop:~/Desktop/Research Data(All)-
2nd's Out put::::::::::::::::::::::::::::
 Sardar Kh a and requested for asylum...Depending on what command you typed, this would be what you'd expect to see. For instance, **find -name "*.doc" -exec antiword -t {} \;** would just dump the contents of each matching file to stdout. (See antiword's man page.)

> **true_friend said:**
> ss@ss-desktop:~/Desktop/Research Data(All)$ 5~for f in *.doc; do antiword -t $f; done
bash: syntax error near unexpected token `do'A typo may have caused this error.

To create individual text files, rather than having antiword dump them to the console, you could try something like **find -iname "*.doc" -exec sh -c 'antiword "{}" > "{}".txt' \;**

---

### Post by true_friend on 2007-04-17
thnx it worked just fine.

---

