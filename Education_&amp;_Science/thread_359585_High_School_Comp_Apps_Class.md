---
title: "High School Comp Apps Class"
date: 2007-02-12
forum: Education &amp; Science
---

### Post by MatthewMetzger on 2007-02-12
Hello,

I'm teaching a Computer Applications class in a private high school. I had the class build two computers from stock components and then we installed xubuntu (on the slower machine) and ubuntu on them (latest versions) .

What do you think are some good activities to teach basic computing knowledge and skills using the ubuntu operating system? I've got a few in mind, but I would love to hear ideas from other people.

-Matthew

---

### Post by MatthewMetzger on 2007-02-13
Well, I'll share a few of my ideas since no one is commenting.

Right now my students are learning about networks and the internet. The ubuntu computers are isolated, not connected to the larger school network. I'll use the computers, with a switch, to show them how computers can be connected together. From there, we'll install routing software on one of them and demonstrate DHCP. DNS is also a very important concept and can be demonstrated by setting up a DNS server. DNSmasq can do all of this and isn't terribly difficult to understand.

Has anyone else used Ubuntu in education, specifically in teaching students about computers and technology? I'd love to hear your experiences.

---

### Post by hizaguchi on 2007-02-14
I guess it depends on what you want them to get out of the class, but I'm a mechanical engineering student and learning the basics of math scripting back in high school would have been extremely helpful for college.  You could teach them to solve algebra problems with simple iterative techniques like Newton's method in something like Octave or Scilab.  It's a valuable skill outside of computing too, because it changes the way you look at math in general.

---

### Post by finer recliner on 2007-02-14
> **MatthewMetzger said:**
> Well, I'll share a few of my ideas since no one is commenting.

Right now my students are learning about networks and the internet. The ubuntu computers are isolated, not connected to the larger school network. I'll use the computers, with a switch, to show them how computers can be connected together. From there, we'll install routing software on one of them and demonstrate DHCP. DNS is also a very important concept and can be demonstrated by setting up a DNS server. DNSmasq can do all of this and isn't terribly difficult to understand.

Has anyone else used Ubuntu in education, specifically in teaching students about computers and technology? I'd love to hear your experiences.

i like the networking idea.

---

### Post by maxamillion on 2007-02-14
You might try setting up LAMP or just Apache and letting the students do some basic web development, maybe install a ftp server to demonstrate its functionality, and another option if you would like to get deep into networking fundamentals I recommend setting up a [GNU Zebra]("http://www.zebra.org/") box to teach router administration.

Another option would be [eBox Platform]("http://ebox-platform.com/") in order to show a wide array of server capabilities (though it would require debian sarge installation as opposed to Ubuntu, but I'm sure the older machine would suffice for this)

I have taught some people slowly and steadily, alot of it was more specific to just linux (debian/ubuntu) administration, things like package management from the command line and explaining what was actually happening, showing them some basic bash scripts, letting them add and remove users/groups in order to get the familiar with bash in general, etc... just stuff like that.

---

### Post by MatthewMetzger on 2007-02-15
> **finer recliner said:**
> i like the networking idea.

It worked fairly well. I did the demonstration on Wednesday because it was "block day" (hour and a half classes). The concept of Domain Name Resolution was very effectively illustrated by having the class give the computers funny names. When the dns server was turned on they could access the other computer using the name, but couldn't when dnsmasq was turned off. I set up apache using apt-get and had them access it from the other computer.

It worked fairly well. This is the beginning of a unit on networking and the internet (it is more of a general class and isn't very math intensive).

thanks for all your suggestions.

-Matthew

---

### Post by MatthewMetzger on 2007-02-15
> **maxamillion said:**
> You might try setting up LAMP or just Apache and letting the students do some basic web development.

I do plan on doing this later. It will be an example of how a set of instructions tell the computer what to do (even if it is only display as HTML would be).

We'll also install and use some web applications like mediawiki and wordpress when we study web applications (such as google search and amazon.com's store).

-Matthew

---

### Post by TheShadow99 on 2007-02-22
Hello,

I would be interested in hearing more about your plans as next school year I will be dealing with a after-school program with a similar concept at the charter school I work for (though I'm the network admin, not a teacher).

We have plenty of old hardware so I'm more than willing to teach them how to put together their own PC from parts (in groups) and then learn how to make that PC work. I did have a thought about using the LEGO robotics kits as well to do some basic programming with real world results...

If you'd liek to talk about ideas send me a message...

---

### Post by in_flu_ence on 2007-02-25
Since it is high school computer class and I presume those interested somehow know how a PC functions (in terms of Windows), i guess i will do the following.

1) Intro the OS and list the feature comparison to windows. (Bring them to the Linux world)
2) Intro the FOSS softwares like Openoffice, Email clients etc.
3) Go specific softwares like those in the Education package (chem, physics, cad,etc)
4) Project work to utilise the software from contructing their flow diagram to presentation.

All the above is meant to make sure they are competent linux users and move away from the Windows.

5) Go for command lines. (Sample install pacakge and remove package).
6) Debugging
7) Introduce Python to write simple scripts
8) System Management (E.g. manage network, manage user group, etc).

This is basically to bring them to a new level to enhance the experience and be competent to help others. Python will allow them to have creative thinking and very useful when they move on to the university in future (engineering especially).

Just m thought.

---

### Post by stream303 on 2008-03-10
> **in_flu_ence said:**
> 5) Go for command lines. (Sample install pacakge and remove package).

Yes!  This will not appeal to some, quite a few in fact, but I've found the problem with attracting people to the command line is that it is presented in such a way as to be a total turn-off.  Here are my ideas on how I came to like it, even though I'm not a raving fanboy about it. :)

Present it as a **skill** that you can retain, since the cli is not going away or changing much!  Many of the commands we use now are just as applicable to us now as when they were first implemented 40 years ago!

The big point here is that you are learning something that you won't waste your time on - something that was a big worry to me when I was in HS.   A lot of interfaces have come and gone in the meantime, yet the secret of the commandline is it's simplicity!  It can be much like learning to ride a bicycle.

Yeah, right.  Just take a look at all those commands I have to remember with all those switches!  It seems overwhelming.

The solution is to take it easy and realize that you are* learning a language*; one that can stay with you your whole life.  It may not be a programming language, but just the basics of the shell language can go a long way.  Aside from Linux, I know many who don't realize that they have a nice shell and a typical editor like nano and vi on their Macs right now.

Where to start?  Start with the personal stuff, things they can do if they only become hobbyists, and not system administrators.

The basics of getting around the filesystem with ls, mkdir, rmdir, cd, less, more, come to mind.  Follow up with some simple desktop-type apps like cal, and bc.
Introduce file editing.  Perhaps start off with nano, but for my money, at some point graduate them to vi, if the students can wrap their heads around a modal editor.  If I had learned vi back in 1979, I'd have 29 years of file editing experience behind me.  The time I spent learning it was not wasted-time, since I plan to be using vi another 20 years from now.  Try that with some other editor.  (please, this is an example only, not meant to be an editor flamewar.  Substitute your own legendary editor here if you like.  However, when the chips were down where I worked, vi was *always* available.)

Introduce find, grep, sort, and perhaps a smattering of sed and awk so that they can create lists of their own stuff, and manipulate them.
Of course also introduce redirection and piping.
Although it isn't a standard, if you need a spreadsheet, try a little "sc" from the repos.

How do you "sell" the cli?  Point out that the user him/herself is the interface.  It is raw and direct, like some of the music I enjoyed earlier on. :)  Nobody is telling you how to use it, it is up to YOU.

What time is it?   date
Can I see you next Friday?  cal

Or you can click on 5 different things to pull up the calendar in Evolution. :)

I think you get the picture.  Reintroduce the toolbox-concept that made *nix great in the first place, and a total hit at the universities.  Create your own tools and solutions, rather than being wrapped up in a pre-define box of someone else's making.

Well, I didn't want to turn this into a rant, but did want to point out that time spent in the command line is not a wasted effort, or one that is going to change just a few years down the road.

Perhaps challenge the upcoming students by seeing just how much they can get out of a server install that doesn't even have a gui interface available, or perhaps the simplest of window managers like twm just so they can look at images with imagemagick by using the cli:  display mygradschool.jpg

Guess I better stop before I look foolish - might already be too late. :)

---

