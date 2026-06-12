---
title: "Tricky links in e-book application (children education)"
date: 2021-09-08
forum: Education &amp; Science
---

### Post by janeku2 on 2021-09-08
Hello.
The son is using electronic textbooks starting this school year. The Ministry of Education has attached to their official website a working application (opening and reading books) that runs under Windows and Android platform. They has also published books packed in zip format. The zip file contains the book itself and under the subfolders is the multimedia part of the book (videos and music records, quizzes, etc.). 
The application under Windows to be able to work with it completely, during the installation adds C ++ elements from the C ++ redistribution package, installs Chrome and installs a small program httpd.exe (It seems that the Apache server part is also used because the whole program is installed in the folder c: \ apache)
**The problem: **The books themselves are readable in any pdf reader BUT opening the links via any pdf reader (not through the installed software and Chrome) on the pages where there is multimedia activity and which lead to the multimedia files, redirects to an external link and Chrome (Firefox) gives link error, i.e. does not open anything. 
Now, under Windows, when the same link is opened from Chrome within installed application, the above-mentioned small program httpd.exe performs some kind of redirection of the pages in the book and through the Windows application (where Chrome is the basic browser) they open without any problems.
**Question: **Is it possible to do something similar under Ubuntu (intercept, redirect) and open the listed problematic links without any problem, without using the specified application under Windows (open the book with a regular pdf reader and when the multimedia link is selected, the required multimedia open a file without any problems from under the folder where it is placed) and to be able to work only under Ubuntu not to be forced to use Windows for just this application?

---

### Post by TheFu on 2021-09-11
What are the links that are being followed?  Are they to files, to a localhost URL?

For example, I have a few O'Reilly CD bookshelves that came with a java-based applet that connects to a local java-based webserver. This is used to make searching across different books possible - a browser can't do that.  I just put an entire copy of each "bookshelf" onto a web server and it works fine ... except the searching part. For that, I wrote a tiny search interface that uses recoll as the search engine.  In general, the "index" and ToC all work within the same book, only cross-book searches fail.

There are hacked versions of the O'Reilly CD bookshelves easily found online, but those point to hacked servers too. I assume those provide a back door into the LAN if used.

---

### Post by janeku2 on 2021-09-14
> **TheFu said:**
> What are the links that are being followed?  Are they to files, to a localhost URL?

For example, I have a few O'Reiley CD bookshelves that came with a java-based applet that connects to a local java-based webserver. This is used to make searching across different books possible - a browser can't do that.  I just put an entire copy of each "bookshelf" onto a web server and it works fine ... except the searching part. For that, I wrote a tiny search interface that uses recoll as the search engine.  In general, the "index" and ToC all work within the same book, only cross-book searches fail.

There are hacked versions of the O'Reiley CD bookshelves easily found online, but those point to hacked servers too. I assume those provide a back door into the LAN if used.

Links are usual as follows: 
h*tps://**0008**resources/0008/index.html**%D0%88%D0%90%D0%A1 %D0%98%D0%9C%D0%90%D0%9C %D0%A1%D0%92%D0%9E%D0%95 %D0%9C%D0%98%D0%A1%D0%9B%D0%95%D0%8A%D0%95**audio**mk**4 

And HTML file in each multimedia folder is either size of 1-2kB reffering to something in the folder , or 800kB-3MB and it is usually some interactive quiz itself.

EDIT: If I open index.html in folder itself, it opens reffered document stated in index.html (or quiz trivia).
If I open the same link from book itself it does nothing or reffer to nothing.

---

### Post by QIII on 2021-09-14
The answer to your bottom line question is: "Maybe".

We don't know what that .exe does, how it does it, etc.  It is probably quite simple and straight forward -- if you only knew what it was doing.  

My opinion on things like this is pretty simple and straight forward as well:  If a curriculum requires Windows to be used, use Windows.  There is no station at the entrance to Linux heaven where one has to show proof that they have been strictly true to Linux.  Whatever one's feelings for Microsoft might be, one's education must take priority.  I'd say to support your son in manner least likely to cause any unnecessary difficulty or stress.  

You might have to dual boot Windows.  A VM might work, but there may be some rough video issues to tackle.

Edit:  Seeing your edit -- if that is not too much trouble and it works, that may be the route to take.

---

### Post by TheFu on 2021-09-14
> **QIII said:**
> You might have to dual boot Windows.  A VM might work, but there may be some rough video issues to tackle.


Some things aren't worth fighting to solve.  I've never had problems with CBT (computer based training) that required Windows that running inside a VM that didn't work fine.  I tried to make WINE work with a few key programs for a few years, but that got tiring and a program update broke that solution, so I just have a Windows VM to run programs like that now. That's the easy answer.

Any Core2 Duo or better computer with 4+ GB of RAM can easily run a Windows VM for 1 purpose. That's a 10 yr old Core2 Duo, BTW.

Have you looked up the company who created the ebook platform and contacted them?  Perhaps they have a work-around?  It probably won't do much good to complain to the school - nobody there decided on this software - or they are extremely non-technical, so they don't know the issue.  

In the UK, you might claim to have a Raspberry Pi computer as a desktop and ask for help to get that package working. That could get them thinking about a standards-based solution for spring or next year.  I have a $50 tablet that I'd use for most things like this ... that also doesn't run MacOS or Windows.  The trick is to get the school system to think about other options, especially for a ebook.  I take it they don't support chromebooks in your system?  Here, 50% of the kids are low income and given a chromebook to use for a few years. I don't know when they are expected to provide their own computer - ebooks are PDF and most programs are from MS-Office 365 online (more like 345 here with the outages).

My library system has an Android app to let me check out ebooks, audiobooks, and other media for learning.

My point is that you'll likely need to run Windows for now. Use a virtual machine with virtualbox as the hypervisor.
But you can plant a seed for the future ability to use a raspberry-pi or chromebook/ChromiumOS solution by mentioning in the issue. There might be nearly zero traction on this, but perhaps there are other parents in the school with similar needs?  1 person complaining doesn't usually get anywhere, but if 5 people complain, then the school will listen and future planning can take those concerns into account.

---

