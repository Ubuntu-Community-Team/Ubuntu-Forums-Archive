---
title: "Computer Programming Class for Middle School Kids"
date: 2009-12-03
forum: Education &amp; Science
---

### Post by ctdahle on 2009-12-03
I am starting this thread as a sort of "request for comments", and I would welcome any input that anyone would like to offer. With your permission, I'd like to use this thread as a sounding board for a project I have been working on. In the spirit of open source, I am more than happy to share anything that I develop or discover, and I will be glad of any comments, critical or otherwise that anyone wishes to add.

I am several years into my third career, as a teacher of middle school math and science, and I am very concerned that public school kids do not have sufficient opportunities to learn how to build things or work through projects that require them to do any detailed planning, think ahead, or consider the logical consequences of actions and decisions.

I am working up a proposal to create and offer a computer programming class for middle school students (10-14 year olds). I'm not a programmer by any stretch of the imagination, but I did take high school courses in basic and fortran back in the 1970's so I have some idea of the kinds of ordered thinking and planning ahead that can be taught by learning simple programming skills.

It is my opinion that by offering the kids the opportunity to learn to program computer games, I can hook them into learning the importance of developing a coherent plan for accomplishing a goal, learning to clearly and accurately articulate that goal, transform that goal into a set of logical operations, and convert the operations into accurate instructions for the computer to follow.

I envision setting a series of tasks for the kids that require them to develop and produce a series of progressively more complex games, beginning with something comparable to the "battle ship" or "moonlander" games of the TRS-80 days, and progressing to "flashier" tasks from there. 

In order to do this, I am going to have to put my self to school a bit, and after sniffing about, I am leaning in the direction of teaching myself Python, with an eye toward using PyGames as a teaching platform. Obviously learning Python myself will be one of the critical preliminary tasks, so  any guidance on that would be welcome as well...and if you think Python is the wrong choice, I want to hear that too.

Moderator...if this is in the wrong place, or you want to move it, please feel free to do so.

---

### Post by Lars Noodén on 2009-12-04
Sounds exciting.

I'm relieved to see Python there.  For tools, I'd skip the big, heavy IDEs and use Kate or even Geany.  They have a nice little text box that can be used to run the scripts and a fair amount of support for general programming.  

If you are looking for them to make some graphical programs, then look at the Ubuntu package python-qt4 and maybe also python-qt4-gl.  The latter gives OpenGL support for python, [OpenGL](http://www.opengl.org/) being **the** standard for 2D and 3D video. 

For databases, stick with something very simple like Sqlite or even (plain, not xml) BerkeleyDB.  

The performance of Python will be limited, so don't expect any FPS.  But they might be able to make a mobile phone app or two.

---

### Post by gnuman on 2009-12-05
> **ctdahle said:**
> It is my opinion that by offering the kids the opportunity to learn to program computer games, I can hook them into learning the importance of developing a coherent plan for accomplishing a goal, learning to clearly and accurately articulate that goal, transform that goal into a set of logical operations, and convert the operations into accurate instructions for the computer to follow.....


Hi!

First of all: welcome and thanks for recognizing the need for this in education.  I myself went from teaching math full time at the high school level to only teaching AP Calculus now, with the rest of my classes being programming classes.  I have many resources that you'd be welcome to look at, so just PM me.  For starters, try [Al Sweigart's book]("http://inventwithpython.com/index.html"), which is great at paying tribute to old computer games like you may have written in the past.

My only caution would be this: focusing on games per se will attract boys to the class, and maybe one or two girls.  I've found that offering classes aimed at creating art or animation tend to attract both boys and girls, and the boys will find ways to make games whereas the girls might write programs for a different purpose.  If this isn't a concern for you, go with your heart.  There are so few qualified teachers that want to teach programming, so anything you offer that you believe in will make the world a better place.  :)

I teach an Intro to Programming class that uses [Alice, from Carnegie Mellon University]("http://alice.org/").  I then have a full-year course that uses Python, and I also teach AP Computer Science.  I absolutely love Python, and would recommend heavy use of [Gregor Lingl's new turtle module]("http://docs.python.org/library/turtle.html") and [John Zelle's great graphics module]("http://mcsp.wartburg.edu/zelle/python/graphics/graphics/index.html").

I have a lot of things I've used in the past that you're welcome to see.  For my current classes, you can look at my teaching site and find some of the stuff we're doing there.  I started this as a hobby (simply a programming club) a few years ago and it has grown huge by now.  I have also been lucky to have the National Science Foundation give a grant recently that will bring doctoral students in computer science to work with me in my classes and further developing curriculum, for the next five years.  :o

Forgive my fanatacism:

You are not alone in seeing a need and wanting to help out.  Since you posted here, I assume you see the merit of open source, and I can tell you that you're on the right track.  Please look open source first and avoid any offers from proprietary companies that may contact you.  Sure, they'll offer you free copies and benefits, but only with open source can you be sure your students can go home and freely install the same software and never have to deal with annoying EULAs.

Good luck and if you need more resources, I have a ton.  There is a small community of comp sci teachers that are working together to deliver what we believe are excellent classes in programming that are much better than your typical "learn MS Office" or "create web pages with Dreamweaver" classes you see so all too often.

---

### Post by swisscow on 2009-12-05
+1 for Alice. Kids love it

---

### Post by hubie on 2009-12-07
gnuman can comment on whether this would be appropriate for middle school, but gnuman pointed out a couple of very nice looking programs, [Processing ]("http://processing.org/")and [VPython]("http://vpython.org/index.html"), [over in another thread]("http://ubuntuforums.org/showthread.php?t=1344534"), that look like they'd be great as teaching languages.  There looks to be plenty of examples from which to start modifying and learning.

I also thought the comment about focussing on computer art or animation to avoid unintended gender selection is very important.  Women are very underrepresented in my field (physics), and this is true in many technical fields.  The disparity issue has been studied a number of times and, from what I recall, they mostly show that girls start to drop interest in science and math in middle school.  There very well could be true physiological reasons for this (e.g., "women's brains aren't wired for math and science"), but I have worked with and have been around enough very sharp and adept women in math and science that I believe societal effects are more dominant than physiological.

---

### Post by ctdahle on 2009-12-13
Thank you for the thoughts and ideas. I have not forgotten about this thread but it's the last ten days before Christmas Vacation and I manage 168 12-year-olds...

---

### Post by goldshirt9 on 2009-12-14
an interesting thread.
I've learnt a lot myself through the  links.
*I'm hoping my 12 year old son *will have a go at the programming side.

---

### Post by euler_fan on 2009-12-15
My first programming class (freshman year of high school) used C++. 

Ultimately you're going to need to pick the curriculum and then pick the language for the pairing to be effective. I haven't seen too many people arguing for using Java to teach low level algorithm stuff nor C++ or FORTRAN for web development.

---

### Post by m_b on 2009-12-18
Have you looked at Scratch? It's designed by MIT to be a teaching language specifically for kids as young as 8 years old. Even the young at heart will be able to learn programming basics with it. You'll learn programming basics along with the critical thinking skills that come with programming. 

You program games, stories, interactive art, and multimedia projects by snapping color-coded blocks together. It alleviates syntax errors and kids see immediate, easy results; therefore, having a better experience. 


Scratch also makes it easy to import multimedia into projects from a webcam, photos, sound files, or record your own audio directly into the project. 

There's also a big online community built around Scratch with lots of sample code for your students to remix. 

Scratch website: [scratch.mit.edu]("http://scratch.mit.edu")
Ubuntu Installation:[ http://www.scratchguide.com/]("http://www.scratchguide.com/install-scratch-on-ubuntu/")

---

### Post by Lars Noodén on 2009-12-19
@ euler_fan : if you mix C++ with Qt or GTK+ then you have the makings for some fun mobile programming on Maemo.  Android apparently uses Java.

---

### Post by ctdahle on 2010-02-12
I didn't want to leave this thread an orphan...

The whole project is more complex for me than I expected and has lead in many interesting directions.

I discovered that I did not know anywhere near enough about programming, so I have been devoting much of my time to learning Python. I am working my way through John Zelle's book *Python Programming:An Introduction to Computer Science*...an excellent textbook by the way. Learning to program is fun and challenging, but I do wish I'd been able to do it when I was 20 instead of 48. I just don't have the uninterrupted blocks of time to figure things out any more and am lucky to get 30 minutes at a time to focus. Maybe learning to play the piano is something to be done in 45 minutes a night, but I'd learn programming more quickly if i could give it two five hour blocks each week...a luxury few modern parents can afford.

Programming turns out to be immensely fun, and I am even more persuaded that a well designed computer science course will be a big draw for middle school kids.

I'm also playing around with ALICE, and Storytelling ALICE, (A project out of Carnegie-Mellon) experimenting on my own kids with the latter. Unfortunately, Storytelling ALICE is not ported to Linux and doing that job is beyond my current skill-set. Maybe someone here will pick that up!!!!

The real hurdle however, is "proving" that my computer programming project will help kids succeed within the "standards based" multiple choice testing environment of the NCLB and my state's "Annual Yearly Progress" model of school assessment.

---

### Post by gnuman on 2010-02-13
> **ctdahle said:**
> 
....Unfortunately, Storytelling ALICE is not ported to Linux and doing that job is beyond my current skill-set. Maybe someone here will pick that up!!!!

The real hurdle however, is "proving" that my computer programming project will help kids succeed within the "standards based" multiple choice testing environment of the NCLB and my state's "Annual Yearly Progress" model of school assessment.

I have had pretty good luck running the beta version of Alice 3 on Linux.  Because it contains the Sims 2 characters, it is well suited as a storytelling app.  Also, feel free to check out [my course pages]("http://futureskyline.com") for my Intro to Programming classes.  I have archived material from the past, also, if you pm me I can show you where.

I don't know how the US will stay competitive with a total lack of any focus on computer science in our schools.  I am one of the few that lucked out and was allowed to develop an entire cs curriculum at a large public high school.  I've done so with the help of a NSF GK12 grant that brings cs doctoral students to my school to work with me and my students.  I have a Principal that encourages computer science.  Without that, I'd still be teaching math full time and sponsoring a programming club.  Contact me if I can help you in any way.  

This will have to be a grassroots revolution, methinks.....  :-)

---

### Post by ctdahle on 2010-02-15
Thank you Gnuman, I have been looking through your pages. I wish I was in your classes. I'll follow up with a PM when I know better what i am talking about.

I have the day off so I am digging deep into the Zelle book today.

---

### Post by adgators89 on 2010-03-05
Thank you guys for motivating me!  I am new here and just started using Edubuntu about three weeks ago.  I am a technology teacher jjust becoming familiar with linux through this distro and I love it so far.  It is exciting to learn something new.  now I have become very interested in programming (never had any programming classes) and without any experience I already would love to introduce it to my students.  I see that the python book is an excellent resource as mentioned in the above posts.  I am interested in starting with the kturtle program.  I also saw the mention of scratch and processing, but would need guidance in all of it.  Is there anyone out there willing to teach a newbie with high interest level?

---

### Post by Adam Redwine on 2010-03-06
I would agree with many of the other posters that Python is a great way to go.  I've also used Qt quite a bit and, though I haven't combined the two with PyQt, I imagine it would be a good pairing.

More than anything else, I'd stress the need for incremental success.  If the kids put together code, and it doesn't work within a couple attempts to fix it, they are going to get frustrated.  This is going to generally make graphical programming difficult, but some of the suggestions about scratch and such might be worth following up on.

If you have any students with a particularly strong feel for it, you might introduce them to something like sagemath (which uses Python).  If you show them not only how programming can be fun, but how it can actually be useful to them, I think you'll have better longterm success.

As I'm currently applying for Teach for America to teach math and science, I'm particularly interested in what happens.  It'd be great if you'd keep us posted.

---

### Post by ctdahle on 2010-03-20
A critical element of teaching anything to kids is teaching them how to learn on their own. Much of what kids will need to know 20 years from now hasn't been invented or discovered yet, so once kids can read, write, and calculate accurately (and we should expect them to have that mastered by 5th grade) they should begin to learn to direct their own learning. One way (the best I think) is to introduce them to interesting fields of inquiry so that they develop a thirst to explore further on their own, and to then provide them with tools and opportunities to explore at levels that challenge their understanding.

I try to introduce kids to new areas of discovery by modeling my own investigations into new areas, and always having something new and interesting on my plate that I can share with kids. Most topics in Science, Technology, Engineering and Mathematics can be approached at several levels so that they are challenging to kids of multiple ages and abilities, and to adults as well.

Computer programming is turning out to fit well into this model, and it branches off into many areas that hold appeal for kids. Game programming, storytelling, virtual reality, along with robotics and other forms of physical computing all have "hooks" that can draw kids in.

I struggle with the need to learn "all" of it in order to identify areas that will hold appeal for kids of differing interests and abilities; I need to have a general understanding of the basics of many areas from astronomy to zoology. But I also need to have detailed understanding in a variety of areas as well, and to teach kids how to discover and develop their own detailed expertise in an area that interests them.

I've been busy teaching myself Python with the Zelle book, and also working through the SICP "Wizard" book and the CS-1 lectures that MIT has made available online. Beginning this next week, I am going to start working with one student using the "Hello World" Python book by Warren and Carter Sande. It will be more of a partnership, we will meet once a week and we will each do the practice programming in the chapters and grade each other's work. "Hello World" leads in more of a game direction than the Zelle book, and probably is better for 10-12 year olds. I hope to use my learning from this to build a core group that will become the 13-14 year old leaders of a STEM club and eventually a more formally recognized and organized STEM learning program.

However, I have also been diverted by robotics in the last few weeks. I took my own kids to a robotics workshop two weeks ago where I was introduced to the potential of small robots to stimulate inquiry in math and engineering. There too, I was urged to look at Arduino, so I purchased one of them, along with a kit of robot parts.

The robot kit's microprocessor is programmable in a dialect of Logo, but it has limited capabilities. More promising is the Arduino, and one of my objectives is to learn how to wire and program Arduino to emulate the functions of the microprocessor that came with the robot kit.

Arduino, as you all probably know, but I am just learning, is programmed in a variant of C++, so the robot project has added two more programming languages to my plate, along with the need to relearn some basics in electronics that I never really understood the first time around (in the 1970's).

Fortunately, there has never been a time in history when it has been easier to obtain detailed technical knowledge with a brief, but intensive application of effort.

Anyway, if I can inspire a few kids to study robotics, a couple of others to investigate game programming, a handful more to explore the sky with a telescope, some others to experiment with different ways of growing plants...if I can come up with activities that draw kids into exploring just one thing in depth and detail, then I believe they will discover, on their own, the need to be skilled readers, effective writers, accurate mathematicians.

Cheers,

---

### Post by megahost on 2010-03-22
If you are intending to teach Python as a first language, that will be a little hard on the students. I wouldn't recommend teaching students python as a first language, but maybe something more simple, like VB. Other than that, I support you.

---

### Post by ctdahle on 2010-03-23
I agree that Python probably is a bit much for the littlest kids to start, but I am learning to use some other tools to help them see what computer programming is about.

Kids are not going to be impressed by writing a script that translates Celsius to Fahrenheit, or sends "Hello World" back to the monitor. They need more dramatic and dynamic feedback. I am playing with robotics for this reason. Initially, I thought I had blown it by buying a robot kit that turned out to have been somewhat abandoned by its manufacturer and a limited, but graphically based programming environment. However, this turns out to be an asset.

The kids experience initial success using the simple graphical programming tool, dragging and dropping icons to control the robot's movements, learning how to communicate with the hardware and developing stronger logical thinking skills.

Then they want to push the boundaries of the graphical environment and find that as their program becomes more complex, the graphical environment becomes awkward and limiting. They then are exposed to the greater capabilities of a more powerful programming language. Once they are able to apply a library of text based commands and understand the demands of syntax and structure, they are ready to dig in to more powerful languages and different sorts of tasks.

From there, they should be ready to move in several directions (Alice for animation, Python for tasks like game programming, C for robotics...) and have the intellectual tools to judge for themselves which language is best suited for the task they wish to accomplish.

I thank you all for continuing to follow this dialog. It keeps me moving forward.

---

### Post by caucauman on 2010-07-20
Hi Gnuman

I would like to see the resources that you mention in your posting. How do i get to your teaching site?.

Gonzalo

---

### Post by Sef on 2010-07-21
> Hi Gnuman

I would like to see the resources that you mention in your posting. How  do i get to your teaching site?.

Gonzalo 	

GNUman wrote  >   I have archived material from the past, also, if you **pm me** I can show  you where.

Note: Bolded the appropriate text.

---

### Post by coolman98 on 2010-10-01
use python I would love your class im a kid interested in python so.
def best_choiche = python
#include<python is is best.>

---

### Post by gotMAD on 2010-10-05
i whish they had this at my school in middle school

---

### Post by addy digit on 2010-10-06
Your kids also need to use the computer daily for schoolwork at this age, and it's not practical for you to sit next to them as they work. You're not sure how you feel about the time they're spending on the computer each day.......
This lesson is designed for parents of middle school students. You can find more information in our Technology and Your Student course, and you'll find age-specific tips in our other Quick Lessons for parents of elementary and high school students.:)

---

### Post by wsande on 2011-03-03
You might want to check out our book:

"Hello World!  Computer Programming for Kids and Other Beginners"

[http://www.amazon.com/gp/reader/1933988495/](http://www.amazon.com/gp/reader/1933988495/)

[http://cp4k.blogspot.com/](http://cp4k.blogspot.com/)

Several educators (mostly middle school) have used it with their classes and had great success.

I, also, worry that the US will not be able to stay competitive with no focus on computer programming in the curriculum.  This is our small contribution to the grassroots effort.

Regards,
Warren Sande

---

### Post by Lektorvis on 2012-01-14
Hi I see this thread is turning in to a commercial board, so I won't hesitate to promote two fine non-commercial game makers for 4th -7th grade.
The must intuitive programming editor for kids and teenagers is Scratch. The programming is done with coloured bricks representing the different functions an methods and classes. 
You will find it installs easy on Ubuntu. The program is developed by people from MIT.
See more:
[http://info.scratch.mit.edu/]("http://info.scratch.mit.edu/")

If you are running 64bit Ubuntu look here: [http://info.scratch.mit.edu/Scratch_on_Linux]("http://info.scratch.mit.edu/Scratch_on_Linux")

Greenfoot is a step further up the learning ladder, but still intuitive and with a flat learning curve which makes it an ideal program in classes with students on different levels. 
Greenfoot is developed by people from University of Kent and La Trobe University with support from Oracle so off cause the language written is Java. 
See [http://www.greenfoot.org/download](http://www.greenfoot.org/download) 

Both programming editors have active forums for educators. 

I'm a high schoolteacher and I always start beginner classes with Greenfoot, before I move on to Php, Python or any other OOP language.

---

### Post by davidmilsont on 2012-01-19
It's a interesting thread. Computer programming is one of widely used in a I.T sector and It might help kids to take bright their future.

---

