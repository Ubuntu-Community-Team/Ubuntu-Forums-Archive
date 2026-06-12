---
title: "Homework Client Needed"
date: 2013-01-02
forum: Education &amp; Science
---

### Post by rudeboyskunk on 2013-01-02
Ok, this is a bit long, but bear with me.  The basic gist of this post will be my need of a web-based program that allows university students to do their homework online and submit it through the program, which automatically checks for correct answers and lets the professor know their score and whether or not they actually did it.

First, a little background:

I teach ESL at a university in South Korea.  Our department has 40 lecturers in it, all from one of the seven standard English-speaking countries (USA, UK, Ireland, Canada, Australia, New Zealand, South Africa).  We are looked down upon by all the other departments and thus receive less funding.  Therefore, over the past year we have been working to completely revamp our image and the way we run things in order to look and become far more professional, as well as to ensure that our students are getting top-grade English education (every student is required to take two semesters of ESL to graduate).

One problem we have is homework.  Why is it a problem?  We have 15 weeks of classes (-2 for exams, so really 13), so ideally that should be 13 homework assignments that the students do (once a week, natch).  However, some lecturers never assign homework, some assign it a few times, and some assign it every week.  In addition, there's no standard homework we're giving (we all just give our own -- keep in mind that these students are strongly evaluated to determine their level and to make sure they join the appropriate level class, so there is uniformity across different lecturers).  Every lecturer has approximately ~100 students for these classes, so assuming every student does their homework, that's 100 sheets of homework a week to grade.  Those lecturers who give homework usually just give grades based on who actually did the homework rather than if it was correct or not.  In addition, many students don't do the homework ("I was absent last class so I didn't get it," "I left it at home," etc), and a lot of them will just copy it off of their friends 5 minutes before class begins, sometimes in front of the lecturer (whenever I see that, I tell them to leave the class and that they're absent for the day).

We've come up with a solution, but it only goes halfway and makes things worse in some ways.  We've [finally] set up a website for our department (I know, we didn't have one before, it's like 1993).  We're making one homework assignment per lesson that is uniform, so every class will have the same assignment, and they're all being made before the semester begins (March 5).  We will upload the homework every week to the website in docx or pdf format so the students can either print it out or do it on their computer and email it.  Now, this will greatly increase the workload of every lecturer 10-fold, and it still doesn't solve the problem of students copying each other right before class.  Having students email it (or even print it out) becomes a logistical nightmare, as there are so many students and it will be done every week (about 30-40 students per class).

Here's MY solution, but it's really ambitious (unless this already exists):  The students do the homework through a form on the department website which automatically scores the homework and tells the lecturer the score, thus getting rid of all the previously-mentioned problems.

Here are the criteria for what I need:

1) Students enter their information into a form (name, student number, select a lecturer from a drop-down list, which activates another drop-down list from which they select which class they are in specifically).

2) Computer automatically checks the answers and tells the students their score, but does not tell them which answers are correct or incorrect.

3) The new homework becomes available Monday morning at 12:01 AM and is due the following Sunday at 11:59 PM.  After the deadline they can no longer access the previous week's homework, but if they did it, they can print out the questions and correct answers (the exam questions will be *based on* the homework questions -- not the same, but using the same vocabulary and grammar -- they can use the homework to study for the exam).

4) Students can view their grades at any time and keep track of their homework score (right now it's only 10% of their final grade, but we're trying to move it up to 20%, which should encourage them to do their homework even more).

5) Every question will probably have to be multiple choice.

6) The scores will be sent to a central folder which is accessed by the lecturers.  The scores are automatically added to spreadsheets of classes which keep track of the students' overall grades.

7) The lecturers' only job is to check who did the homework and who did not, and could, if they wanted, announce at the beginning of class this information.

8) If possible, I would like for the questions and answer selections to be randomized, thus cutting down even more on cheating.  They will all answer the same questions, just in different orders with the answers being in different combinations.




So basically, does this already exist as FOSS?  If not, after I make it, I will release it under the GPL3 (I'm going to check my contract tomorrow to see if I'm allowed to keep intellectual property rights; I don't want my university to claim IPR and then sell it without my permission) so that other schools can use it.

If it doesn't already exist, can anybody point me in the direction of where I need to get started?  I would really appreciate any and all help.

I've got two months to get it through alpha mode on my own, and I'll do beta testing with a few professors and their classes during the spring semester, with hopefully a 1.0 release in the fall.

I think the only requirements will be html, css and possibly java if I wish to institute javascript.  A good knowledge of spreadsheet software will of course help (it's Korea, so we use WinXP and Office 2007 for everything unfortunately).

---

### Post by Kirk Schnable on 2013-01-02
> **rudeboyskunk said:**
> Here's MY solution, but it's really ambitious (unless this already exists):  The students do the homework through a form on the department website which automatically scores the homework and tells the lecturer the score, thus getting rid of all the previously-mentioned problems.
There's not an existing free solution for this which I'm aware of... my university uses MyLabsPlus for the type of interaction you're talking about.

But I will respond briefly to the technical side of your quetions.

> **rudeboyskunk said:**
> 1) Students enter their information into a form (name, student number, select a lecturer from a drop-down list, which activates another drop-down list from which they select which class they are in specifically).
Would not be a big deal to do this as a PHP\HTML form if you had a list of students to import from your student management system, or had students make their own accounts, or created the accounts manually.  You'd just want all of the students in a SQL database table, ideally.

I wouldn't even have them select their instructor.  That should already be in the database.

> **rudeboyskunk said:**
> 2) Computer automatically checks the answers and tells the students their score, but does not tell them which answers are correct or incorrect.
Not a big deal to compare answers with the correct answer in a PHP script, etc.  However, if they made a typo, it would be wrong.  The only way to prevent this is manual grading.

> **rudeboyskunk said:**
> 3) The new homework becomes available Monday morning at 12:01 AM and is due the following Sunday at 11:59 PM.  After the deadline they can no longer access the previous week's homework, but if they did it, they can print out the questions and correct answers (the exam questions will be *based on* the homework questions -- not the same, but using the same vocabulary and grammar -- they can use the homework to study for the exam).
A few time restrictions, etc, would not be a big deal for a PHP system.

> **rudeboyskunk said:**
> 4) Students can view their grades at any time and keep track of their homework score (right now it's only 10% of their final grade, but we're trying to move it up to 20%, which should encourage them to do their homework even more).
Would require keeping their grades in a different SQL table, indexed by some kind of unique identifier like their Student ID and then a unique ID for each assignment.  Again, not a huge deal.

> **rudeboyskunk said:**
> 5) Every question will probably have to be multiple choice.
No big deal, just makes the questions database table slightly more complicated.  Would actually resolve the potential typo problem.

> **rudeboyskunk said:**
> 6) The scores will be sent to a central folder which is accessed by the lecturers.  The scores are automatically added to spreadsheets of classes which keep track of the students' overall grades.
"Folder" is the wrong way to think of it when you're talking about a web script.  You'd want an admin panel that teachers could login to, to view the scores that are in the database.  Similar to the page students use, but showing their whole class.  Again, quite possible in a home brew PHP\SQL solution.

> **rudeboyskunk said:**
> 7) The lecturers' only job is to check who did the homework and who did not, and could, if they wanted, announce at the beginning of class this information.
The page outlined for step 6 could achieve this, or a separate SQL query could make a "completed homework list" just as easily.

> **rudeboyskunk said:**
> 8) If possible, I would like for the questions and answer selections to be randomized, thus cutting down even more on cheating.  They will all answer the same questions, just in different orders with the answers being in different combinations.
This would make the question code slightly more complex, or the test code, but could certainly be done. 

> **rudeboyskunk said:**
> So basically, does this already exist as FOSS?  If not, after I make it, I will release it under the GPL3 (I'm going to check my contract tomorrow to see if I'm allowed to keep intellectual property rights; I don't want my university to claim IPR and then sell it without my permission) so that other schools can use it.
Not that I know of.  Perhaps someone else will have a better solution...but I would make it myself, personally.

> **rudeboyskunk said:**
> If it doesn't already exist, can anybody point me in the direction of where I need to get started?  I would really appreciate any and all help.
If you need any pointers on your database structure or program logic, I'd be happy to bounce some ideas back and forth.   I am experienced enough with PHP\SQL that I could probably sit down and make this.

> **rudeboyskunk said:**
> I think the only requirements will be html, css and possibly java if I wish to institute javascript.  A good knowledge of spreadsheet software will of course help (it's Korea, so we use WinXP and Office 2007 for everything unfortunately).
I would really use MySQL.  Using Excel spreadsheets as a database for a web tool like this would be an absolute nightmare.

You could easily dump the contents of the grade page query, etc, to a CSV file which you could then open in Excel, so I think the approach to take would be creating an "Export" option to dump your data to CSV.  

I don't see any need for Java or Javascript.  Enforcing any limits on the client's web browser is unsafe, because they can tamper with your code.  Personally, I'd do everything in PHP\HTML and style it with CSS.

Again, if you would like to do it my way and have any questions about how to proceed, I'd be glad to give you some help.  I suggest having our discussions here on this forum thread so they can benefit the entire community.

---

### Post by Kirk Schnable on 2013-01-02
This isn't exactly what you described (not as advanced) but you might like [Edmodo]("http://www.edmodo.com").

---

### Post by TheFu on 2013-01-02
a) don't use docx or pdf.  You want the answers entered directly into the system by the students AND you want the profs (or their aids) to enter the questions for each class into the system using industry standard methods. Definitely avoid any data conversions.

b) Why not look for F/LOSS projects that do something like you need before setting your ***requirements***.  I'd check out Freecode.com and Alternative-To.  I'd ask other education institutions how they handle online grading. **DO NOT RE-INVENT THE WHEEL.**  Reach out to other schools with online courses.  Almost every college in the USA has this today.  Also, you can ask the more active Linux Users Groups in larger metro areas the same question. My LUG has a few people that run Linux systems in local colleges and for a primary school system. I bet they'd know the top 3 software tools today.  I vaguely recall  "FLOSS Weekly" [http://twit.tv/show/floss-weekly](http://twit.tv/show/floss-weekly) did a story about online training - that should be easy to find ...

If you have more budget than time, consider contacting an organization that does training professionally.  Khan Academy [https://www.khanacademy.org/](https://www.khanacademy.org/) comes to mind and so does memrise.com  I'm sure they'd love to help out.  Khan provides all sorts of statistics about each student's efforts.

WinXP is almost out of support, so that is a bad idea for everyone.

MS-Office is always a bad idea when LibreOffice works so well. Teach open formats, push ODF format files so almost any productivity software, including microsoft's can be used.

Java and Javascript are not the same. You probably know that, but a sentence implies they are.

I would never accept files from students. I'd make them work online, inside the website - isn't S. Korea the most connected place on earth?  If you must accept batch data from students, I'd force CSV, but it really is best to avoid all format conversions. Nothing good comes from that.

This does sound like a fun programming project, but to be most successful, you really want to avoid programming completely. Your requirements are missing lots of things. User authentication, back-end database(s), different screens for system admins, teachers, students.  Where's the security layer to prevent hackers? This is a college, right? 
This is a much bigger program than you have outlined. Whatever you do, don't use PHP unless you are an EXPERT in PHP.  It seems easy, until you are hacked.

For any subject like a language, the homework needs to be 60+% of the grade.  Learning a language can't be crammed like for a test, it has to be stored in long term memory and used from time to time or it will never stick. Actually just showing up to class is a big part of learning any language. Practice, practice, practice.  

Good luck. I hope those ideas on where to find existing solutions helps.

---

### Post by rudeboyskunk on 2013-01-02
> **TheFu said:**
> a) don't use docx or pdf.  You want the answers entered directly into the system by the students AND you want the profs (or their aids) to enter the questions for each class into the system using industry standard methods. Definitely avoid any data conversions. 

Right, one of the points of my solution is to make sure we don't have to use any files.

> **TheFu said:**
> 
b) Why not look for F/LOSS projects that do something like you need before setting your ***requirements***.  I'd check out Freecode.com and Alternative-To.  I'd ask other education institutions how they handle online grading. **DO NOT RE-INVENT THE WHEEL.**  Reach out to other schools with online courses.  Almost every college in the USA has this today.  Also, you can ask the more active Linux Users Groups in larger metro areas the same question. My LUG has a few people that run Linux systems in local colleges and for a primary school system. I bet they'd know the top 3 software tools today.  I vaguely recall  "FLOSS Weekly" [http://twit.tv/show/floss-weekly](http://twit.tv/show/floss-weekly) did a story about online training - that should be easy to find ...


I will try that out, thanks.

> **TheFu said:**
> 
If you have more budget than time, consider contacting an organization that does training professionally.  Khan Academy [https://www.khanacademy.org/](https://www.khanacademy.org/) comes to mind and so does memrise.com  I'm sure they'd love to help out.  Khan provides all sorts of statistics about each student's efforts.


Unfortunately we have a very small budget, so this all has to be done in-house.

> **TheFu said:**
> 
WinXP is almost out of support, so that is a bad idea for everyone.

MS-Office is always a bad idea when LibreOffice works so well. Teach open formats, push ODF format files so almost any productivity software, including microsoft's can be used.


This is not up to me.  I'm at the bottom of the totem-pole and what I say about information technology will have zero bearing on the decisions that the higher-ups make.  The people in charge of this kind of thing don't even know I exist.

> **TheFu said:**
> 
I would never accept files from students. I'd make them work online, inside the website - isn't S. Korea the most connected place on earth?  If you must accept batch data from students, I'd force CSV, but it really is best to avoid all format conversions. Nothing good comes from that.


Like I said, by doing this, we should no longer have to accept files from students (I personally never would anyway, because that would be a logistical nightmare, and I could never be sure it's coming from a student).

> **TheFu said:**
> 
This does sound like a fun programming project, but to be most successful, you really want to avoid programming completely. Your requirements are missing lots of things. User authentication, back-end database(s), different screens for system admins, teachers, students.  Where's the security layer to prevent hackers? This is a college, right? 
This is a much bigger program than you have outlined. Whatever you do, don't use PHP unless you are an EXPERT in PHP.  It seems easy, until you are hacked.


Right, this is all stuff I haven't thought of, so thank you for bringing it up.

> **TheFu said:**
> 
For any subject like a language, the homework needs to be 60+% of the grade.  Learning a language can't be crammed like for a test, it has to be stored in long term memory and used from time to time or it will never stick. Actually just showing up to class is a big part of learning any language. Practice, practice, practice.  


I am not in charge of setting the grading requirements.


Thanks for your comments.  You've given me a lot to think about.

---

### Post by rudeboyskunk on 2013-01-02
> **Kirk Schnable said:**
> There's not an existing free solution for this which I'm aware of... my university uses MyLabsPlus for the type of interaction you're talking about.

But I will respond briefly to the technical side of your quetions.


Would not be a big deal to do this as a PHP\HTML form if you had a list of students to import from your student management system, or had students make their own accounts, or created the accounts manually.  You'd just want all of the students in a SQL database table, ideally.

I wouldn't even have them select their instructor.  That should already be in the database.


Not a big deal to compare answers with the correct answer in a PHP script, etc.  However, if they made a typo, it would be wrong.  The only way to prevent this is manual grading.


A few time restrictions, etc, would not be a big deal for a PHP system.


Would require keeping their grades in a different SQL table, indexed by some kind of unique identifier like their Student ID and then a unique ID for each assignment.  Again, not a huge deal.


No big deal, just makes the questions database table slightly more complicated.  Would actually resolve the potential typo problem.


"Folder" is the wrong way to think of it when you're talking about a web script.  You'd want an admin panel that teachers could login to, to view the scores that are in the database.  Similar to the page students use, but showing their whole class.  Again, quite possible in a home brew PHP\SQL solution.


The page outlined for step 6 could achieve this, or a separate SQL query could make a "completed homework list" just as easily.


This would make the question code slightly more complex, or the test code, but could certainly be done. 


Not that I know of.  Perhaps someone else will have a better solution...but I would make it myself, personally.


If you need any pointers on your database structure or program logic, I'd be happy to bounce some ideas back and forth.   I am experienced enough with PHP\SQL that I could probably sit down and make this.


I would really use MySQL.  Using Excel spreadsheets as a database for a web tool like this would be an absolute nightmare.

You could easily dump the contents of the grade page query, etc, to a CSV file which you could then open in Excel, so I think the approach to take would be creating an "Export" option to dump your data to CSV.  

I don't see any need for Java or Javascript.  Enforcing any limits on the client's web browser is unsafe, because they can tamper with your code.  Personally, I'd do everything in PHP\HTML and style it with CSS.

Again, if you would like to do it my way and have any questions about how to proceed, I'd be glad to give you some help.  I suggest having our discussions here on this forum thread so they can benefit the entire community.

Great!!  Thanks a ton for all of this advice.  I'm going to be doing a lot of researching on what you've posted over the next week, so I'll come back with what I've got and let you know of any questions I have (I'm sure there'll be plenty).

---

### Post by Kirk Schnable on 2013-01-02
> **TheFu said:**
> a) don't use docx or pdf.  You want the answers entered directly into the system by the students AND you want the profs (or their aids) to enter the questions for each class into the system using industry standard methods. Definitely avoid any data conversions.
Agreed. This is why I suggested a database backend and CSV dumping. 

> **TheFu said:**
> WinXP is almost out of support, so that is a bad idea for everyone.
I'll second that!

> **TheFu said:**
> MS-Office is always a bad idea when LibreOffice works so well. Teach open formats, push ODF format files so almost any productivity software, including microsoft's can be used.
Using LibreOffice will save on licensing costs, as well. 

> **TheFu said:**
> This does sound like a fun programming project, but to be most successful, you really want to avoid programming completely. Your requirements are missing lots of things. User authentication, back-end database(s), different screens for system admins, teachers, students.  Where's the security layer to prevent hackers? This is a college, right? 
I don't entirely agree. While I agree that the original poster's outline of the requirements demonstrates a slight gap between requirements and reality of implementation, I think the project is very doable. At my work, we have numerous home brew solutions which work great, and have been secure. 

> **TheFu said:**
> This is a much bigger program than you have outlined. Whatever you do, don't use PHP unless you are an EXPERT in PHP.  It seems easy, until you are hacked.
As long as you cover your bases, doing it in PHP is just fine. Most of our home brew solutions here are PHP. Just need to make sure you don't make any loopholes, and that you sanitize your inputs.  PHP can be secure enough, but I agree that a beginner programmer might make some obvious mistakes in PHP. 

A pre-existing solution would likely save a lot of time, and may be more secure. Although, plenty of FOSS solutions have loopholes too, and not all are highly maintained.  I implemented eTicket here internally, and I inadvertently found a few SQL injection vulnerabilities... Not all of the free projects are secure, by any means. No matter what you implement, you have to have backups, and be prepared for security holes, as well as being prepared to patch them. 

However, if you've never programmed PHP before, this isn't the kind of project you'd want to sit down and do. It would be overwhelming to a beginner. 

I would look for existing solutions, if possible paid or highly active/used ones, because those solutions will likely be the most responsive to security vulnerabilities you may discover along the way. 

Just my two cents.

---

### Post by Kirk Schnable on 2013-01-02
> **rudeboyskunk said:**
> Great!!  Thanks a ton for all of this advice.  I'm going to be doing a lot of researching on what you've posted over the next week, so I'll come back with what I've got and let you know of any questions I have (I'm sure there'll be plenty).

No problem. I will openly acknowledge that TheFu's concerns are valid ones. Be prepared to spend the time to do this right if you do it in-house. 

That said, this is a doable project, and I'm willing to acknowledge your funding and resource limitations, given that I work in education IT myself, and I'm in the same circumstance sometimes.

If you have any further specific questions as you're doing your research, please don't hesitate to ask!

---

### Post by TheFu on 2013-01-02
> **Kirk Schnable said:**
> No problem. I will openly acknowledge that TheFu's concerns are valid ones. Be prepared to spend the time to do this right if you do it in-house. 

That said, this is a doable project, and I'm willing to acknowledge your funding and resource limitations, given that I work in education IT myself, and I'm in the same circumstance sometimes.

If you have any further specific questions as you're doing your research, please don't hesitate to ask!

I know very little about educational software, but I do know software development, doing things with just TIME (zero budget) and project management.  This is one of those cases where I'd tell the leadership:
> 

[LIST]
[*]Features
[*]Cost
[*]Schedule
[/LIST]
Pick any two.


If there isn't any budget, I'd walk away. This is a no-win situation.  

If you are a student being paid to "accomplish something", that is different. Then there is budget, but I'd be back to my list of F, C, and S - pick any 2.  You have probably heard that before.  **It is true, even when management doesn't like it.**

In-house development is usually more expensive, but it does have 1 thing that is predictable - COSTS.  They will never exceed the monthly budget, but schedule and features are completely out the door.  For in-house developed software the COSTS continue for years beyond whatever is predicted.



Sorry that I'm so negative. I've seen hundreds of these "free" projects fail after wasting lots of REAL money, usually in the form of "time."  People seldom actually work for free.



Every program has bugs. All of them.  What matters is if your users are impacted by the bugs and whether you can do anything about them. F/LOSS lets you have control that you can't get from COTS or a service provider. Selecting a F/LOSS solution that is useable for the students would be my primary goal. I would throw out all the other requirements until I'd researched what the F/LOSS is available.  I believe there is a commercial company buying up all the F/LOSS projects in this area (my memory from that FLOSS Weekly episode is returning slightly), except there is 1 project remaining out of Brazil or Argentina that is still 100% F/LOSS. Sorry, I can't remember the name.



I would strongly encourage that the OP start a dialog with **Khan **too - they may help for free.  At least the dialog would help spell out the level of money involved to the project leaders. It would reset some expectations back to reasonable levels.  That can't hurt the OP either.



Two months just isn't enough time to code all this in any language, though an expert in Ruby or Python or Perl using frameworks he knows very well could get far. I can't see anyone using Java (or C++) getting too far. Those languages just aren't as nibble.  Someone new to this sort of development will be climbing a mountain.  Just sayin'.


I do wish you all the luck with it and hope to be eating my words in 2 months.

---

### Post by forgetfulmonkey on 2013-01-02
This sounds like a job for Moodle:

[http://moodle.com/]("http://moodle.com/")

Looks like it would do everything you want.  You could set up your own Moodle server and then run everything from there.

---

### Post by rudeboyskunk on 2013-01-03
> **forgetfulmonkey said:**
> This sounds like a job for Moodle:

[http://moodle.com/]("http://moodle.com/")

Looks like it would do everything you want.  You could set up your own Moodle server and then run everything from there.

This is EXACTLY what I want.  Even all of the highly ambitious stuff that I want is included.  Thank you so much!!!  Just gotta spend two months getting over the learning curve, followed by a 4-month beta period with a hopeful full release for the fall semester.

---

### Post by TheFu on 2013-01-03
> **forgetfulmonkey said:**
> This sounds like a job for Moodle:

[http://moodle.com/](http://moodle.com/)

Looks like it would do everything you want.  You could set up your own Moodle server and then run everything from there.

I thought Moodle was going commercial?  Perhaps not.

Anyway, did a google on "moodle vs" and found the F/LOSS project I couldn't recall earlier - **blackboard.**  No idea if this is a fit or not.

---

