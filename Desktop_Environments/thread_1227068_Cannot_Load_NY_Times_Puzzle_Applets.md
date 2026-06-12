---
title: "Cannot Load NY Times Puzzle Applets"
date: 2009-07-30
forum: Desktop Environments
---

### Post by Leadbelly on 2009-07-30
[http://www.nytimes.com/pages/crosswords/index.html](http://www.nytimes.com/pages/crosswords/index.html)

This is a link to the NY Times's puzzle page. I use a Ubuntu 8.04 operating system and a Firefox 3.5.1 browser or an Opera 9.64 browser. 

I cannot load 2 puzzles from the puzzle page: the sudoku and set puzzles. There is an applet at the bottom of the page of top ten puzzlers, the 10 folks who most recently solved the crossword. There is an acrostic and a crossword for juniors. There is a chess blog which contains certain games with a chess viewer. I can load and use all of these others, but not sudoku and set. When I try to load these 2, I get a message that files are loading and a spiral of black and white squares which hangs up at some point before completing. After the hang, I usually have trouble closing the browser and need to end or kill the browser and/or the java vm processes. Lots of times I see a residual ghost window which says "Java embedded frame." 

I don't know of any other applets that I can't load.

I am wondering if anybody else can load these applets and play the puzzles and if you can, how did you configure Java?:confused:

---

### Post by mcslim on 2009-08-10
Try cancelling any instances of java (as well as java_vm).  I have the same problem as you (Firefox, Ubuntu, NY Times crosswords).  Started troubleshooting tonight and managed to find success by first killing all Java processes (and all instances of java_vm, as well).  Might be a fluke, but give it a shot.  Maybe we can help each other troubleshoot.

---

### Post by Leadbelly on 2009-08-11
Thanks for replying, mcslim. I have started at thread in the Firefox forums on this topic:

[https://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_parentId=402520#threadId406584](https://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_parentId=402520#threadId406584)

I also wrote to the NY Times about this problem:


[http://www.nytimes.com/membercenter/formh.html](http://www.nytimes.com/membercenter/formh.html) In this form I sent an e-mail regarding crossword puzzles.

I received a reply from:


From: NYTimes.com Customer Service <help@nytimes.com>
Subject: RE:Crosswords -- 4698
Date: Tuesday, July 28, 2009, 7:36 PM

Dear Reader,
 
Thank you for contacting NYTimes.com.
 
The issue sounds like it is going to be with how your browser renders Javascripting, or Java.
 
What I would recommend is making sure that you have the most update to plug-ins for your browser.
 
You can find the links to download the newest plug-ins from here:
[http://www.nytimes.com/ref/membercenter/help/plugins.html](http://www.nytimes.com/ref/membercenter/help/plugins.html)
 
I hope this helps and please feel free to contact us with further questions or concerns.
 
Regards,
 
Andrew Smith
NYTimes.com
Customer Service
[www.nytimes.com/help](www.nytimes.com/help)

___________

Perhaps you might contact the NY Times and perhaps Mr. Smith and the reference to Crosswords 4698 might be helpful. 

I received another reply about 10 days ago telling me that the technical staff was looking into the problem.

---

### Post by Leadbelly on 2009-08-11
I don't have much new to add regarding troubleshooting. I thought I had better luck loading the puzzles fairly early in the morning as opposed to at night, but this morning I couldn't load the hard sudoku even after several tries. I was able to load the set puzzle fairly quickly. There was 1 partial load of the set puzzle which was kind of interesting: I had 12 pale empty gray rectangles and a longer empty green strip across the bottom. The 12 rectangles were in the place the 4 answers would go in the 1st of the 4 set puzzles. The long green strip was where the message "Try to find a valid set." would go. This is the 1st time I have stumbled across a partial load of the set puzzle. I have seen something similar with a hard sudoku load.

1 thing that is maddening about this is that the results are unpredictable. I try to do the same things but get very different results.

I have tried terminating the java processes. 1 problem is that, as far as I know, only the 2 Times' applets cause the java process to terminate abnormally. Even if there is a stray java process or 2 sleeping, I can go here: 

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

and be told that everything is okay with my configuration.

By the way, I am using Firefox 3.5.2 and jdk1.6.0_15.

In any event, the puzzles don't load for me 1st time and every time.

---

### Post by Leadbelly on 2009-10-05
This problem is still not fixed, in that I still cannot load the daily hard sudoku puzzle 1st time and every time.

I 1st contacted the Times's puzzle editor, Will Shortz, about this problem on July 21.

---

### Post by Leadbelly on 2009-11-15
Thank you for your patience.
 
We apologize for the inconvenience, however after forwarding the issue to our technical staff they have informed me that they were unable to offer support for Ubuntu in regards to NYTimes.com, and the online puzzles.
 
They did suggest that upgrading to the most recent version of Ubuntu might offer a potential solution to the issue.
 
Regards,
 
Andrew Smith
NYTimes.com
Customer Service
[www.nytimes.com/help](www.nytimes.com/help)
_______________

This is a copy of the body of an e-mail I received from the NY Times on October 30. I have 1 computer with version 8.04 and another with version 9.10 and I can't load the hard sudoku and and set puzzles 1st time and every time on either computer.

---

### Post by falconindy on 2009-11-15
Works fine, here (64-bit, Sun jdk). Are you using OpenJDK or the closed source from Sun?

edit: i can't read...

---

### Post by Leadbelly on 2009-11-17
The NY Times' puzzle page contains crosswords, acrostics, chess games, sudoku, set, etc.

I have problems only with the sudoku and set puzzles. 

The problems are not as bad as they once were but I can't count on being able to load the puzzles when I want them.

---

