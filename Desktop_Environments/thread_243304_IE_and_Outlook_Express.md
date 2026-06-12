---
title: "IE and Outlook Express"
date: 2006-08-24
forum: Desktop Environments
---

### Post by eyebrow on 2006-08-24
i take classes at University of Phoenix online.  the classes are newsgroups in Outlook Express that i subscribe to.  they dont seem to be compatable in Thunderbird.  also, the schools website (when signing in and downloading class materials) is only compatable with IE and does not work with Firefox.  

Question:  is there any IE based browers that can run in Ubuntu?  is there an alternative mail client that can subscribe to outlook newsgroups?  is there any other way around this like a virtual PC?

---

### Post by ciscosurfer on 2006-08-24
You can certainly install VMWare or Qemu or use Xen and then install XP and use Windows programs that way.  Or you can install CrossoverOffice: [http://www.codeweavers.com/](http://www.codeweavers.com/) and then install the Windows prgrams you need to use and then use them that way.  Both ways work. :)

---

### Post by nalmeth on 2006-08-24
> **eyebrow said:**
> i take classes at University of Phoenix online.  the classes are newsgroups in Outlook Express that i subscribe to.  they dont seem to be compatable in Thunderbird.  also, the schools website (when signing in and downloading class materials) is only compatable with IE and does not work with Firefox.  

Question:  is there any IE based browers that can run in Ubuntu?  is there an alternative mail client that can subscribe to outlook newsgroups?  is there any other way around this like a virtual PC?
That sucks your school is so dependant on windows...
You can install IE in ubuntu, easy way is a script called ie4linux. Google will point you to it.
I think an older version of outlook can run in wine, check out winehq's database for compatibility.

Have you tried evolution with the Outlook stuff?

---

### Post by ciscosurfer on 2006-08-24
IE4linux is not secure

> **nalmeth said:**
> Have you tried evolution with the Outlook stuff?

Using Evolution is a good suggestion.

---

### Post by eyebrow on 2006-08-24
thank you both very much.  i will try all that stuff and let you guys know what happens.

p.s. it does suck that my school is so dependent on MS; you would think that being an educational establishment they would be more openminded.

---

### Post by mikeoh on 2006-08-24
I have the same with my university only supporting IE in a subject so I installed IE using wine and IE4Linux.  Outlook Express works as well under wine.

Sure IE isn't secure but I think it is a reasonable assumption that the unversity website is 'safe' to use.

---

### Post by MrSweet on 2006-08-24
I was also at UoP for some time.  When I first started the classes I was using Windows, then I found Ubuntu and decided to test it out.  I choose to do all my schoolwork in Ubuntu to see how well it worked.  For your classes Thunderbird does work, you just need to set it up to access the UoP servers and have the connectoin secure.  I tried multiply news readers and thunderbird was the only one that would work.  First you need to set up the server information, which you can get from Outlook Express.  Make sure that the address is correct, UoP has around 150 different news servers.  Next you need to make sure that you tell thunderbird to use a secure connection.  This is the only bug.  When I used it it would ask me for my user name and password about 15 times in an hour, even though I had it set to remmeber all the information.  If you get to the pop up password boxes remember to read them.  One will ask for user name and then another one will ask for your password.  (I spent a full night just typing my password in the boxes and got no where.)  

As for firefox, I do not remember having any problems accessing anything for the school.  I was able to see the class list, access the library for research, and get to most anything else.  The only thing that didn't work was the link to go to class.  For me that was not a big deal because I had thunderbird working.  What kind of problems are you having with FireFox?  Maybe I can help you there if you explain a little more.

I hope this helps you.  If not then give a little more detail as to what is happening and maybe I can help get you going.  Oh, one more thing.  No one in my group had any problems with my open office files.  They were all able to open and edit them for classwork, so you don't need to worry about using MS Office.

Mr. Sweet

---

### Post by eyebrow on 2006-08-25
i can sign in and look at everything with firefox, its just when i try to subscribe to the classes.  specificly after i click the red link below the class listing that says "subscribe to class", then it takes me to the page with the green start button, clicking on the button goes to the page with the subscriptions: it doesnt do much after that.  the subscription links never show up; just a blank page that says "please wait...".  it works fine in IE, i get nothing in firefox

how exactly do i "set up the server information, which you can get from Outlook Express"?  when i look in the properties of outlook it says "C:\Documents and Settings\derty\Local Settings\Application Data\Identities\{CE07CDD3-8CC3-4845-9E71-993A88D9C9A1}\Microsoft\Outlook Express\AAB6.08-07._AAAA03B6T9-IT300.dbx" is where the newsgroup is stored.  i know its called "AAB6.08-07._AAAA03B6T9-IT300", but thunderbird wants something that looks like "news.example.net"

also, its nice to have someone who has been through this helping me.  thanks.

---

### Post by MrSweet on 2006-08-26
When you are in outlook, you need to go to the acounts menu.  If you clicked the link in IE it should put the news account information in outlook express for you.  I am not using windows right now, so I have to do this from memory, but there is a section in the drop down menus where you can access your e-mail account settings.  There should be a row of tabs accross the top.  One will say News.  If you click that it will show the current news servers that you have.  Just select it and click on properties.  There you will find the address informatino for the UoP server.  Once you have that information you can put that address into thunderbird.  From there just get a list of the newsgroups on that server and subscribe to the ones for your class.

The reason this is not working is because UoP is using an Active X control to put the account information into Outlook Express.  FireFox does not have any Active X controls to use.  Personally I think this is a good thing.  \\:D/ 

I hope this helps you.  Let me know if you have any success now.

Mr. Sweet

---

### Post by geetarista on 2006-11-25
Hey MrSweet, thanks a bunch for all the info.  I've been taking classes for about 6 months and I've always wished there was a way to do it all under Linux.  I've just successfully finished setting everything up in Thunderbird and I'm so excited!  No more Windows AT ALL!!!!

However, it will be short-lived because I know that UoP is going to be rolling out a new online system that allows you to do everything through a web interface.  One of my friends is attending AXIA college of University of Phoenix and they are already using it.  I had her log in to Firefox and try it out and everything seemed to work fine.  I looked through the help files and it seems like it supports Firefox, Camino, Safari, and Opera as well.  The interface is very nice and it will make things much easier for doing the classes online.  Right now there slowly rolling it out for certain programs and it should be all out within a couple of months.

---

### Post by MrSweet on 2006-11-25
Geetarista,

While this could be a good thing for most users, I do hope that UoP still has an option.  My wife attends the Art Institute right now and has some online courses.  They use an all web interface instead of standared news groups.  She has spent hours just trying to figure out what post are relevent to her group and the topic at hand instead of actually writing back to here class mates.  The interface that they use is very bulky and hard to navigate.  If they had a newsgroup option it would take me half the time to find the relevent information with a filter instead of clicking endlessly on a web site.

I just like to have the option to use what I like.  I guess that is why I went to Linux.  This OS just gives me options while others do not.

Mr. Sweet

---

