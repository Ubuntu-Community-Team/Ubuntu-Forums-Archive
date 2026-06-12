---
title: "Finding and displaying a single word in a text file in Ubuntp 8.10"
date: 2009-02-11
forum: General Help
---

### Post by Rossthorne on 2009-02-11
Hi i need some help with this question and its really giving me a headache.  

I have created a text file for a school lab in Ubuntu and in text mode i need to find a command that will find and display the  word only that starts with the letter b and not the entire line.  I didnt know if there was a way to do this with a single line command or not.  If there is a way to write a script or if there is a command that can do this can somebody please help me.


Thanks Ross

---

### Post by HermanAB on 2009-02-11
Pipe grep and cut.

Cheers,

Herman

---

### Post by Dr Small on 2009-02-11
Say, you two wouldn't go to the same school would you? :D
[http://ubuntuforums.org/showthread.php?t=1066811](http://ubuntuforums.org/showthread.php?t=1066811)

---

### Post by braingram on 2009-02-11
I think you can do this using regular expressions and grep. Here is a brief introduction (the first site found when I googled 'grep regular expressions'):
[http://www.robelle.com/smugbook/regexpr.html](http://www.robelle.com/smugbook/regexpr.html)

For example if the name of the file is 'bar' and...
the file is all lowercase:
```

grep 'b[a-z]*' bar -o

```

If the file contains lowercase and capital letters:
```

grep '[bB][a-z,A-Z]*' bar -o

```

The magic is in the -o option. From the grep manpage:
>        -o, --only-matching
              Print  only  the  matched  (non-empty) parts of a matching line,
              with each such part on a separate output line.

---

