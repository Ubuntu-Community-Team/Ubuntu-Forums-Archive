---
title: "I'm going to be teaching Community College Linux, want some suggestions"
date: 2011-11-18
forum: Education &amp; Science
---

### Post by lastaxionhero on 2011-11-18
Hey everyone, next semester I'm going to be teaching Intro to Linux/Unix out at the local community college.  

The class is basically an introductory class for Programming majors.   I'm pretty excited and a little nervous at the same time since this will  be my first time teaching and I'm trying to think of ways to make the  class fun and easy to follow, also I'm still relatively young (25 but I  look like I'm 19) so I need to make sure that they take me seriously.   I'm looking for any tips from educators who have taught on the subject.   I'm also looking for general suggestions on activities that could keep  the class interesting.

the book I'll be using is "Linux+ Guide to Linux Certification" by  Eckert and Schitka and the class will be 2 hours 2 days a week.  The  book is very CLI based with only one chapter briefly discussing X.  It's  got all of your typical content like the the file system layout, GRUB,  basic scripting etc.  It introduces new commands along with redirection  and piping as it progresses.  The distro on the school machines is  OpenSuse.

I plan to demonstrate the content in the chapters at the beginning of  the class, showing how the various commands could be used in a real  world setting.  Considering the students know almost NOTHING about  linux, or CLI's in general (I don't know why the school doesn't  emphasize this) i plan to simultaneously demonstrate the GUI method with  the CLI command so they can understand the power at the Command Line.

I plan to:
-start with a brief introduction on the GUI making comparisons with what they are used to with Windows.  
-I want to introduce Yast early and explain the benefit of a package  manager and how to add repositories.  I feel like this will allow them  to quickly jump into some of the projects I have lined up for them.
-From here I plan to teach the commands and concepts introduced in the chapters, hopefully covering a chapter per week.
-I want to have a quiz every 3 weeks on the material covered
-Every two weeks I will have a project that they need to complete in  class and allow me to access over the network.  I plan to have them work  in teams of two to set up and properly secure things like squid,  apache, and ftp servers.  I plan to answer questions and give help as  needed with these projects.  I plan to count these projects as test  grades instead of having traditional tests.  I'm more concerned about  them tinkering with the OS since it is an intro class and I feel like  hands on experience is the best way to learn.  
-I plan to have pop assignments for extra credit and whatnot such as  "whoever can boot into runlevel 3  and create a directory with a blank  text file at the root of the drive within 5 minutes gets 10 extra points  on their next quiz."  

I understand that Linux can be tough to grasp at first so I do plan to curve if necessary.  

What do you guys think?

---

### Post by lykwydchykyn on 2011-11-18
If they're programming majors, emphasizing the fact that the shell is an interactive interpreter and not just a "command line" might be an eye-opener.

What I mean is, make sure they learn about things like flow control, variables, functions, and other things that make the shell more than just a pile of obscure commands.


Just my 2 cents.

---

### Post by MG&amp;TL on 2011-11-18
Get them writing BASH scripts or something. Emphasize that linux and unix are free, and the advantages thereof.

My favourite BASH script of the moment:

```
 while true; do fortune | cowsay; sleep 5; done
```

Just emphasize that linux and unix can be fun. See if you can get them using it on their laptops/computers, even if it's only wubi.

---

### Post by Lars Noodén on 2011-11-18
> **lastaxionhero said:**
>   I plan to have them work  in teams of two to set up and properly secure things like squid,  apache, and ftp servers.  

I'd skip the [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) and focus on SFTP instead.  The SFTP client is build into FileZilla, Nautilus and many others, plus there are tools like SSHFS.  

It sounds like a server-oriented class.

---

### Post by lastaxionhero on 2011-11-18
> **lykwydchykyn said:**
> If they're programming majors, emphasizing the fact that the shell is an interactive interpreter and not just a "command line" might be an eye-opener.

What I mean is, make sure they learn about things like flow control, variables, functions, and other things that make the shell more than just a pile of obscure commands.


Just my 2 cents.

thanks for the input.

Since this is a second year course, I would hope that they understand the logic behind  the things you mentioned.  I'll just have to show them the correct syntax for declaring variables and creating control structures for BASH to interpret.  I'll make sure I find a good use for a function too.  

I think I may start a script from the beginning and keep adding to it as new commands are introduced.  I This will hopefully reinforce to them that scripting can make repetitive tasks simple.

---

### Post by lykwydchykyn on 2011-11-18
> **lastaxionhero said:**
> thanks for the input.

Since this is a second year course, I would hope that they understand the logic behind  the things you mentioned.  I'll just have to show them the correct syntax for declaring variables and creating control structures for BASH to interpret.  I'll make sure I find a good use for a function too.  

I think I may start a script from the beginning and keep adding to it as new commands are introduced.  I This will hopefully reinforce to them that scripting can make repetitive tasks simple.

Sounds good; I think the "programmability" of the shell is what makes it a really awesome tool, rather than just a harder and less visual way of doing what you can do in any other OS (or in X11) with a click.

You might want to read Eric Raymond's ["The art of Unix Programming"]("http://www.faqs.org/docs/artu/") if you haven't; it's a really great primer on the "Unix philosophy", and helped solidify my understanding of why things are done they way they are in Linux.  Maybe even a good reading assignment for the students.

---

### Post by SeijiSensei on 2011-11-18
Since OpenSuse is a KDE-based distribution, you might want to show them a GNOME-based distribution as well.  One common "aha" moment comes when people realize that the GUI and the OS are separate entities.  Most people coming from Windows are used to thinking of them as monolithic.

I'd spend a bit of time on backing up systems with rsync. This is a good introductory task for scripting and will acquaint them with cron and automated processes.

If you have some time, a bit of exposure to databases like PostgreSQL (my preference) or MySQL might be appropriate.  If they are likely to be programming in PHP some day, knowing how to connect to a database, run queries, and display the retrieved information in a web page is an important skill.

---

### Post by cbowman57 on 2011-11-18
[LIST=1]
[*]Don't get preachy.
[*]Avoid too much pro-linux bias.  (No Windows sux) :)
[*]Assign a homework assignment to install a distro of their choice, then have each student take the podium & explain what they learned, liked, disliked about the experience &/or the distro or DE.
[/LIST]

---

### Post by Bonster on 2011-11-18
Since you're going to be showing them a lot of command lines. That can get boring to many students quick. So once in awhile talk about a cli app they can use for fun/entertainment.

like ex:
cmus
pianobar
shell-fm
irssi
weechat
centerim

etc...


oh yea one thing that i love is the bashrc file
bash alias and functions, it made my cli experience better =)

---

### Post by lastaxionhero on 2011-11-19
> **Lars Noodén said:**
> It sounds like a server-oriented class.


Well the "server setup as a test grade" formula is the model that the head of the department used when he taught the class.  I guess his goal with this formula was for the students to gain some more practical skills since Linux will be more commonly running on servers than it will on desktops in the workplace.  Unfortunately scripting is barely mentioned in the textbook.  I should have mentioned earlier that this class is also part of the IT curriculum.  
        
My goal is to have one dedicated machine running all of the services by the end of the class, and allow the students to remotely manage it, most likely with Webmin.

> **SeijiSensei said:**
> 
I'd spend a bit of time on backing up systems with rsync. This is a good  introductory task for scripting and will acquaint them with cron and  automated processes.


^^ 
I really like this 

Thanks for all of the advice everyone

---

### Post by CharlesA on 2011-11-19
What book at they using? I would think that a Linux book would at least mention a little on scripting. Especially in a book for an IT class.

Also +1 to rsync. I've got a few scripts set up to do that and they can get a tab complicated once you start adding variables and whatnot, but it's a very nice learning experience since you can't exactly break stuff. :P

---

### Post by lastaxionhero on 2011-11-19
> **CharlesA said:**
> What book at they using? I would think that a Linux book would at least mention a little on scripting. Especially in a book for an IT class.


The book is "Linux+ Guide to Linux Certification" 
here's a link 

[http://www.google.com/products/catalog?hl=en&cp=35&gs_id=4m&xhr=t&q=linux%2B+guide+to+linux+certification&tok=BYrhax7GU5hJFIIg69puvg&safe=off&biw=1024&bih=506&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&um=1&ie=UTF-8&tbm=shop&cid=3524357564945655876&sa=X&ei=MsvHTuIgk762B_zUxdEL&sqi=2&ved=0CIMBEPMCMAE](http://www.google.com/products/catalog?hl=en&cp=35&gs_id=4m&xhr=t&q=linux%2B+guide+to+linux+certification&tok=BYrhax7GU5hJFIIg69puvg&safe=off&biw=1024&bih=506&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&um=1&ie=UTF-8&tbm=shop&cid=3524357564945655876&sa=X&ei=MsvHTuIgk762B_zUxdEL&sqi=2&ved=0CIMBEPMCMAE)

[FONT=Arial,Helvetica]
[/FONT] It's geared towards Comptia's Linux+.  I haven't taken it so I'm not sure if there's anything scripting related on the test.  I'm kind of doubtful though knowing Comptia.  IO redirection probably, but scripting I doubt it.

---

### Post by CharlesA on 2011-11-19
I haven't taken that one either, but I guess it's more of a guide to getting the cert and not a general *nix book.

There's a good book on scripting, but I cannot recall the name except that it's refereed to as the "green" or "blue" book.

I think it was published by either Sans or O'Reiley.

---

### Post by haqking on 2011-11-19
> **lastaxionhero said:**
> The book is "Linux+ Guide to Linux Certification" 
here's a link 

[http://www.google.com/products/catalog?hl=en&cp=35&gs_id=4m&xhr=t&q=linux%2B+guide+to+linux+certification&tok=BYrhax7GU5hJFIIg69puvg&safe=off&biw=1024&bih=506&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&um=1&ie=UTF-8&tbm=shop&cid=3524357564945655876&sa=X&ei=MsvHTuIgk762B_zUxdEL&sqi=2&ved=0CIMBEPMCMAE](http://www.google.com/products/catalog?hl=en&cp=35&gs_id=4m&xhr=t&q=linux%2B+guide+to+linux+certification&tok=BYrhax7GU5hJFIIg69puvg&safe=off&biw=1024&bih=506&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&um=1&ie=UTF-8&tbm=shop&cid=3524357564945655876&sa=X&ei=MsvHTuIgk762B_zUxdEL&sqi=2&ved=0CIMBEPMCMAE)

[FONT=Arial,Helvetica]
[/FONT] It's geared towards Comptia's Linux+.  I haven't taken it so I'm not sure if there's anything scripting related on the test.  I'm kind of doubtful though knowing Comptia.  IO redirection probably, but scripting I doubt it.

I have taken it, scripting is not really covered ( i say not really covered though) you wont be asked to write a script, but you could be shown a script and asked to find the error, they are straight forward though.

---

