---
title: "Is there a program to alphabetically order words?"
date: 2009-03-10
forum: Education &amp; Science
---

### Post by Mashuteichou on 2009-03-10
I need this to organize words, obviously, so I can find what I need when I want.  Like, if I am looking for an A word, I don't want to have to search 300 words to find that A word.  

So, is there a program, or a program that has an addon, to simply type a set of words in, and hit a single button to organize them in alphabetical order?  

This would be greatly helpful.  

Thank you for any help.

---

### Post by Functional_Fooled on 2009-03-10
Really quickly (and I am new to this so it may not be as easy as I think) you could save a simple test file of the list of words you want and then convert the unsorted list of words into a text file.  Then enter something such as:

```

cat unsorted_list|grep -f list_of_words|sort

```

replace unsorted_list with the list you wish to filter and sort, and list_of_words with a file that is your list of words.

---

### Post by WW on 2009-03-10
I think the essential part of the previous post is the [sort](http://en.wikipedia.org/wiki/Sort_(Unix)) command. Check it out.

---

### Post by ahmatti on 2009-03-11
> **Functional_Fooled said:**
> Really quickly (and I am new to this so it may not be as easy as I think) you could save a simple test file of the list of words you want and then convert the unsorted list of words into a text file.  Then enter something such as:

```

cat unsorted_list|grep -f list_of_words|sort

```



Its in fact easier than you think ;)

```

sort unsorted_list >sorted_list

```

---

### Post by amac777 on 2009-03-11
You could also use the spreadsheet program, Openoffice Calc. 

Type all the words down one column, select the range, and then call Sort (Data->Sort) to sort them. 

[http://openoffice.blogs.com/openoffice/2008/04/sorting-data-in.html](http://openoffice.blogs.com/openoffice/2008/04/sorting-data-in.html)

---

### Post by WW on 2009-03-12
*The reason for this post has been fixed, so I'll just make it a big ``Thank You!'' to the tireless moderators.*

---

