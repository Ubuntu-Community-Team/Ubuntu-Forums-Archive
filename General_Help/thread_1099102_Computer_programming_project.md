---
title: "Computer programming project"
date: 2009-03-17
forum: General Help
---

### Post by sp176 on 2009-03-17
I was hoping someone here might be able to give a little direction for me.  I wish to work on a personal project that will search an web site with a specific keyword, and that would return info, (probably a database) which in turn I could extract key data and sort it however I wish.  This is also on a website where the info is not in RSS format.

This would be similar to how a hockey pool would run. Have a database for each player, but there would not be one person manually entering all the data, so the program would have to find the hockey player's stats from the nhl or elsewhere.

I have computer programming experience in C++, pascal, and I am an engineer graduate, so feel free to be technical to me.

I have been looking at SQL, and I understand their functions in calling a database, but I dont know how this language is compiled, or how it could search a website.  If I am on the wrong track let me know.

If I need to learn a new language, that is no problem.  This is gonna be a hobby for me.  Python is good, I am just starting to learn now.

Much appreciated.

---

### Post by Peasantoid on 2009-03-17
Hey there. This sort of question actually belongs in the [Development & Programming](http://ubuntuforums.org/forumdisplay.php?f=310) board, but I'll get you started.

SQL is strictly for database management. You can't build a website with it, although it can be used as part of the back-end of one. Go check out [PHP](http://www.php.net/) &#8212; if you're familiar with C/C++, you should feel right at home.

---

### Post by sp176 on 2009-03-18
Much appreciated.  I looked for the proper category to put this, I guess I missed the development and programming one.  Glad this caught your eye though.  I read the website, and it looks perfect for what I need to do.  

I wasnt planning on setting this up as a website for public use, but it seems like I need to set up my own server, and Ive never done that.  Hopefully it is straightforward.

---

### Post by fieroboom on 2009-03-18
The biggest question I would ask is what do you plan to do with the data? PHP is mainly web-driven (yet still multi-purpose), whereas something like python or perl (my personal favorite) might be more tailored to your needs if you're not planning on driving a website with the data... Then the only server you would really need to set up is the MySQL server, which is pretty much a breeze.
:D
-Paul

---

### Post by sp176 on 2009-03-18
Initially I wanted to set up 2 things.  A sports pool for my friends that we usually do, but its slightly different that what you would find on the internet so we have to usually look up stats ourselves.  Also, I play poker, and there are many websites out there that track stats that I use, but it can be a pain to use.

Simply put, I want to be able to:

Enter a name(s)
Perform search
Retrieve data
Sort data
Display

This is all done by the websites, but I want them personalized, and easily referenced.

---

### Post by fixitdude on 2009-03-22
If you are extracting stuff from a web page I would use perl, it's made for that sort of stuff. Go look up some tutorials and sample programs that sort of do what you want. It's easier to take something close and modify it.

You can run it locally on Ubuntu in terminal mode so no need for a server.

Since you like poker, you might want to check out this perl script
[http://ubuntuforums.org/showthread.php?t=1103613](http://ubuntuforums.org/showthread.php?t=1103613)

---

### Post by Xiong Chiamiov on 2009-03-23
The term to search for is "web scraping".  There are many libraries that will make this much easier than doing it by hand.

---

