---
title: "Social Sciences and Statistics (Help Needed)"
date: 2009-02-17
forum: Education &amp; Science
---

### Post by kuniyori on 2009-02-17
Hi everyone.

I'm trying to do a statistics project on usage of wikipedia. I was wondering if there was any software for ubuntu that would allow me to gather statistics from a database dump of wikipedia without the need for programming knowledge.

Its a politics essay to study the development of a community. I would have liked to base it on the growth of the Ubuntu community but I wouldn't know where to begin (wikipedia is much better documented through the use of database dumps). Any advice or ideas on the project would also be of great help:popcorn:.

Thanks!!

PS I know there have been numerious other studies done on wikipedia from which I could take the information i need but I really want to start from scratch to learn how to go about applying the same techniques to other situations and communities. (I'm such a nerd!!!:D)

---

### Post by gunksta on 2009-02-17
I'm sure it's possible if you are willing to do some programming. But, I can't think of any tools that can extract data from Wikipedia, without doing some programming.

If you aren't willing to do some programming, I suggest Googling for growth of Wikipedia user base of something. I'm sure someone has done this before.

It might also help for you to understand exactly what a database dump is. When you acquire a db dump, you are actually getting two things. You are getting the information in the database AND you are getting all of the SQL needed to recreate the database locally on your own machine. In the case of Wikipedia, this means you will be downloading a SQL file that will let you recreate a specific portion of Wikipedia's database on your local computer.

The only way this information is useful is if you are willing to develop SQL queries to extract the specific information you are interested in. And, this would require some basic programming (SQL).

This should give you something to think about. Check back in if you would like to go further.

---

### Post by kuniyori on 2009-02-17
Thanks!

Small problem.... Its not so much that I don't want to do any programming its that I don't know how to. I'm trying to boost my proficiency with the command line first before I move on to something like programming (or at least that was my hope :P ) but its just as well to start in the deep end.

Lots of people have done studies on wikipedia but its more to learn for myself how the study was conducted so from that point of view if I have to learn how to do queries on SQL then so be it ;D !! 

PS Its not that I'm ment to know this already its a self appointed topic just incase anyone is wondering. I study government and social policy and I want to contrast Robert Putnams work on the decline of social engagement with the rise of online communities. One of his books is called 'Bowling Alone' the title of my essay is 'Maybe people just don't like bowling!' so I think you can get the angle I'm comming from... :D

---

### Post by gunksta on 2009-02-17
Interesting idea. As I recall, Putnam does more than merely state that there has been a decline, he also posits possible causes and problems associated with a decline in civil society. (This is all from memory, it's been a while since I earned my Poli-Sci BS).

I like your basic angle and I do think that on-line communities such as Ubuntu, Wikipedia, etc. are now important parts of civil society for many people. But, there are some extra things I think you need to consider.


[LIST]
[*]The classical texts on civil-society were, by definition, constrained to national boundaries. Online communities are not affected by national boundaries, although they are affected by language, cultural norms, etc. Thus, if you want to really understand how much Wikipedia influences Americans (for example) you would need to constrain your numbers to IP addresses that appear to originate from the US (including Puerto Rico, DC, Alaska and Hawaii). Otherwise you are comparing apples to oranges.
[*]How do you compare the value of on-line communities to real-world communities?
[*]How does the Digital Divide affect this participation? For example, go into a public library (in America at least). You will see a line of people waiting for a few minutes on the computer. I am going to hazard a guess that most of the people who participate in the Ubuntu community do not do so from the public library. Thus, the digital divide plays an important role in defining who can and can not participate in these communities. (Other factors such as education, socio-economic status, etc. all play into the digital divide. The library riff is just an example.)
[/LIST]
The more I think about it, I think you should try to do something around Ubuntu. It hasn't been done before (that I know of) and would thus be more interesting. But, it may involve a little hacking here and there to get at some interesting answers.

Either way, your first step is to develop your measurement. You need to define EXACTLY what your measures are for participation. Here's a quick (and imperfect) example (I don't want to be too helpful). You could develop a method to measure how many unique IP addresses contribute to Wikipedia articles in a single month. You could then draw a line graph that shows (I assume) that the number of unique IP addresses increases over time. You could then compare the number of contributors to the number of articles on Wikipedia during the same time frame.

Without looking at the Wikipedia database more carefully, this may or may not be possible. I dunno.

Similarly, you could count the number of "active" members on the Ubuntu Forums. Compare that to the number of downloads / "sales" of Ubuntu (of each release). You will (I hope) see that there are more members today than there were back in the Breezy Badger days. I assume there have been more downloads / Ship It CDs too.

But, I'm not sure how hard it would be to count active users. You could PM a couple of moderators for help. If you could talk to the people who run the Ubuntu Forums, I'm sure they could help give you the numbers . . . you just have to ask the right people!

So do a little digging and a little thinking. Wikipedia has a lot of information available about there articles and such. And I believe they make the IP addresses of people available as well. If you can find the information location / structure I'll help you write the SQL.

enjoy.

---

