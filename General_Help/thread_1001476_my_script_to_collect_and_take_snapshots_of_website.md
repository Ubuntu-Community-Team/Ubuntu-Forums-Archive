---
title: "my script to collect and take snapshots of websites"
date: 2008-12-04
forum: General Help
---

### Post by meg23 on 2008-12-04
I was stuck in the airport the other day without wireless for a few hours and I got to thinking how cool it would be to have an rss feed client that actually downloaded webpages so they could be viewed offline kind of like a web version of miro. 

I found this firefox add-on that allows you to take screenshots of webpages from the command line. So I spent this afternoon coming up with a pretty hacky script that grabs a bunch of URL's off of google news and downloads them to your desktop. To run my script you must download the add-on:

[http://pearlcrescent.com/products/pagesaver/]("http://pearlcrescent.com/products/pagesaver/")

Download the pagesaver basic, which is free.

Once you have the add-on installed, all you have to do download this file and extract it into your home folder and click run_websaver.sh within the folder and firefox will open and close opening the pages and downloading them as png files.

Anyways, If anyone is interested in this project, please help me make this less hacky and perhaps work towards something that is rss based. I think this could be a neat project. 

Enjoy...

---

### Post by strider1551 on 2008-12-04
Interesting.  I've heard other people wish for an rss client that saved the pages locally before.

If you do want to develop this into a serious project, have you thought about doing it in something other than bash?  Bash is great for quick, custom scripts, but it doesn't go much farther than that.  An actual rss client would be much better off written in something like python.

---

### Post by meg23 on 2008-12-04
yeah i agree with you on writing it in python. it is really is the best language to develop these projects in. i do know some python but i would really need some help from some more experienced coders in python. i rely on the import os module too much because i find it difficult to find python versions of bash tools that i am so familiar with. basically what i would like to do is just get something similar working in python and then expand upon its capabilities. you don't happen to be an expert in python do you

---

### Post by strider1551 on 2008-12-04
Well, I would never claim to be an expert, but I should definitely be able to help you with this.  Let me know if you would want to take a stab at this / how I can help.  I'll send a pm with my email.

---

