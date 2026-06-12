---
title: "Learning PSPP"
date: 2009-10-20
forum: Education &amp; Science
---

### Post by satimis on 2009-10-20
Hi folks,


I have PSPP running including the graphic mode.  I'm starting learning it by following;

PSPP manual
Table of Contents
[http://www.gnu.org/software/pspp/manual/pspp.html](http://www.gnu.org/software/pspp/manual/pspp.html).


It is NOT easy for a beginner.  However there is NO manual on graphic mode.


Has any folk learned PSPP before please help.  TIA


As I know PSPP is equivalent to SPSS.  Does the documentation of the later apply to PSPP?  Where can I find relevant documentation to follow?  Thank


B.R.
satimis

---

### Post by gunksta on 2009-10-21
Unfortunately, I learned on SPSS. In my limited experience with PSPP, the dialogs are nearly identical in terms of layout to SPSS, although SPSS is a more mature product. This means that SPSS contains more dialog boxes and menu options than PSPP, but the ones that are there are a very near match with SPSS.

For basic use, I think a SPSS tutorial would be perfectly OK. There are many many first-time-use guides to SPSS on the Internet already.

In fact, if you find one that is licensed with a CC style license you could take it and replace the screen-shots with PSPP screen shots and stick it up here.

The PSPP mailing list is active, but is dominated by syntax discussions and the occasional development discussion. That being said, I'm sure they would respond to a requests for help with the GUI.

This forum is another alternative. I think there are more R users here than SPSS users, but the GUI is straightforward enough I'm sure I can remember the basics.

Unfortunately, a forum or mailing list lends itself more to helping with code than with a GUI simply because it is easier to post the code and discuss than it is to post screen shots or write detailed descriptions of how to interact with a GUI. But, there are plenty of examples that run contrary to this idea, so don't be shy about asking for help.

---

### Post by satimis on 2009-10-21
> **gunksta said:**
> Unfortunately, I learned on SPSS. In my limited experience with PSPP, the dialogs are nearly identical in terms of layout to SPSS, although SPSS is a more mature product. This means that SPSS contains more dialog boxes and menu options than PSPP, but the ones that are there are a very near match with SPSS.

For basic use, I think a SPSS tutorial would be perfectly OK. There are many many first-time-use guides to SPSS on the Internet already.

In fact, if you find one that is licensed with a CC style license you could take it and replace the screen-shots with PSPP screen shots and stick it up here.

The PSPP mailing list is active, but is dominated by syntax discussions and the occasional development discussion. That being said, I'm sure they would respond to a requests for help with the GUI.

This forum is another alternative. I think there are more R users here than SPSS users, but the GUI is straightforward enough I'm sure I can remember the basics.

Unfortunately, a forum or mailing list lends itself more to helping with code than with a GUI simply because it is easier to post the code and discuss than it is to post screen shots or write detailed descriptions of how to interact with a GUI. But, there are plenty of examples that run contrary to this idea, so don't be shy about asking for help.
Hi gunksta,

Thanks for your advice.

I have both PSPP and R boxes here.  While I started learning R I found a vacancy which I'm interested to apply.  However it needs experience on SPSS.  For such a reason and to cope with market demand I turn to PSPP.  The manual of PSPP is mainly syntax operation.  The market needs GUI operation.

I found following thread;

[http://www.ats.ucla.edu/stat/spss/](http://www.ats.ucla.edu/stat/spss/)

I don't know whether it is the right track for me to follow and where shall I start.  Could you please shed me some light.  TIA


B.R.
satimis

---

### Post by gunksta on 2009-10-21
Another good source is:

[http://www.spsstools.net/](http://www.spsstools.net/)

This is the site I use when I'm trying to remember something on SPSS.

The site you reference looks like a good resource too.

I don't know what kind of work you do or how much time you may spend in SPSS but learning the syntax is much more useful than learning the GUI. The GUI may be convenient for a few rounds, but the data-set I'm playing with started with over 300 variables (gotta love big surveys). There ain't no way I'm building all those tables by hand.

I've decided to use R, because I'm more comfortable with it, and I can use tricks like odfWeave to build a report without a bunch of hand formatting/copy-paste but SPSS/PSPP could have done the analysis too.

Here's a really useful tip - By default PSPP will give you a file called pspp.jnl (I think that's the file's name). This little file contains the syntax "written" by the GUI as you pressed the buttons. There have been times when I couldn't remember the syntax, so I did it once, to get it right and then I copied the pattern.  :-)

SPSS can do the same thing, but IIRC, you have to enable it in the options. PSPP does this be default, which I think is better for people trying to learn the system.

---

### Post by satimis on 2009-10-28
> **gunksta said:**
> Another good source is:

[http://www.spsstools.net/](http://www.spsstools.net/)

This is the site I use when I'm trying to remember something on SPSS.

The site you reference looks like a good resource too.

I don't know what kind of work you do or how much time you may spend in SPSS but learning the syntax is much more useful than learning the GUI. The GUI may be convenient for a few rounds, but the data-set I'm playing with started with over 300 variables (gotta love big surveys). There ain't no way I'm building all those tables by hand.

I've decided to use R, because I'm more comfortable with it, and I can use tricks like odfWeave to build a report without a bunch of hand formatting/copy-paste but SPSS/PSPP could have done the analysis too.

Here's a really useful tip - By default PSPP will give you a file called pspp.jnl (I think that's the file's name). This little file contains the syntax "written" by the GUI as you pressed the buttons. There have been times when I couldn't remember the syntax, so I did it once, to get it right and then I copied the pattern.  :-)

SPSS can do the same thing, but IIRC, you have to enable it in the options. PSPP does this be default, which I think is better for people trying to learn the system.

Hi gunksta,

Thanks for your advice and links.

I tried following the movie on;
[http://www.ats.ucla.edu/stat/spss/notes_old/default.htm](http://www.ats.ucla.edu/stat/spss/notes_old/default.htm)

I found it difficult to follow.  The items on the tool bars of PSPP and that of SPSS are not the same.

I think it would be better for me to start learning the syntax commands.  Could you please advise where shall I start on following;

[http://www.gnu.org/software/pspp/manual/pspp.html](http://www.gnu.org/software/pspp/manual/pspp.html)

TIA

B.R.
satimis

---

### Post by gunksta on 2009-10-28
After looking at a few places on the Internet, I think the UCLA site that you found earlier would be a good place to start, but it's not going to be perfect. PSPP has only implemented part of the SPSS syntax and thus doesn't always work like SPSS.

I suppose you could just read the PSPP manual from one end to the other after reading some very simple introductory texts to SPSS.

Unfortunately, I learned SPSS years ago and then discovered PSPP a couple of years ago, although I still don't use it as my primary platform.

---

### Post by gunksta on 2009-10-28
I'm going to PM you with a couple of things that I can't post here.

---

### Post by satimis on 2009-10-29
> **gunksta said:**
> I'm going to PM you with a couple of things that I can't post here.
Hi gunksta,

Please read my PM to you.  Thanks

satimis

---

### Post by gunksta on 2009-10-29
SPSS/PSPP syntax is a little odd compared to more generic programming languages. When I visualize what I am doing in SPSS or PSPP, I basically "see" a spreadsheet on steroids. From this assumption, everything else makes a lot of sense. 

The command syntax, which is a little funky looking (remember your periods at the end and the space before \) but is pretty straightforward. Using the GUI, make yourself a simple data set. 4-5 variables and no more than 10 rows. So, you can start by making a dataset that has variables such as:

[LIST]
[*]First Name
[*]Last Name
[*]Age
[*]Gender
[*]Hobby
[*]Place of Work
[/LIST]
Use your friends and co-workers to fill in this little gem. Remember to use labels for Gender. (You should use the second tab on the bottom of the main screen for creating your variables). 1=Male, 2-Female. Do something similar for hobby and place of work.  Oh yeah - I recommend coming up with better variable names than what I show here. Anywho. Once you have created the variables, you can type in the entries in the first tab on the main page.

One thing that I do like about PSPP/SPSS is how it is easy to visualize the data set. R/Python/SQL can all do the same thing, but I do like the presentation of the data in SPSS. I also like how PSPP will export ALL of your commands to ~/pspp.jnl. This is THE BEST WAY to see the inter-relationship between the GUI and the syntax. It's also a drop-dead easy way to learn SPSS syntax.

Once you have created your data sets, you can play around with the GUI or go straight to the meat of things and open up the syntax editor and write your own syntax. Come up with some things you would like to do BEFORE you start playing around. Try making a CROSSTAB to compare the median age of men and women in your data set. If you want to use PSPP/SPSS I assume you want to build crosstabs! You can use the GUI or the syntax. If you get stumped, start a new thread and ask away. You're more likely to get a good answer if you include your data set. Forums are a great way to learn syntax like this.

Good Luck!

---

