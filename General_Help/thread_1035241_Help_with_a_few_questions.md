---
title: "Help with a few questions"
date: 2009-01-09
forum: General Help
---

### Post by Wovaki on 2009-01-09
Hello!

I'm getting ready to install Ubuntu on my HD, I have been using Wubi for about a month, and I really like Ubuntu.

I do have a couple questions though. First of all, I am just learning some stuff about programming and web design, and on Windows I use Dreamweaver for editing webpages, Photoshop for editing photos and for programming, I have been working with VB.NET for 1 year, and I know a little bit of C++.

So what I'm wondering is:

**1. Are there any programs somewhat like Dreamweaver that are good for making webpages?**
The thing I would miss the most is the autocomplete, and the little list that pops up when I start typing, its good for me because I'm still learning about web development.

**2. Are there any good photo editing programs that would kind of resemble or feel like photoshop?**
I tried GIMP, but I did not really like the layout of it, having the toolbars in the way of the picture.

**3. What should I do for programming?**
I was planning on moving from VB.NET to C#, and then eventually to C++. But if I move to Linux I can't use VB.NET or C# (as far as I know) and I don't think I'm quite ready for C++ yet. I would also like to make applications for both Windows and Linux eventually.

**4. Could anyone reccomend me a good IDE for programming in Linux?**
I was looking at some stuff on here for programming in Linux, and to me it looked like you had to write the source in a text editor or something, then use the terminal to compile it...at my current programming level I think that would drive me crazy.

Thanks for all the help, if I posted this in the wrong section please let me know.

---

### Post by namdung on 2009-01-09
1. U can actually use Dreamweaver upto CS3 in WINE.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=183](http://appdb.winehq.org/objectManager.php?sClass=application&iId=183)
However, in the FOSS world u may try out various options like, *Kompozer, Bluefish, gEdit*

2. GIMP is an excellent alternative to Photoshop. It's a matter of getting used to the toolbars with time.

3. The FOSS world has the Mono project as an alternative to MS.Net Framework. U may program is C# using the Monodev IDE. Mono is available in the Ubuntu repository (Synaptic Package Manager)
[http://www.mono-project.com/](http://www.mono-project.com/)
However, I don't see any reason that why u shouldn't be ready for C++ if ur ready for C#. Java?

4. There are several IDE available depending on ur requirement:
*BlueJ, Anjuta, Eclipse, MonoDevelop, Kdevelop*. All except BlueJ is available in Ubuntu repository.

---

### Post by SteveDee on 2009-01-09
Gambas would be good for you as you have been working with VB.

GIMP is great! But it took me a long time to get used to it after using PaintShopPro for so many years....so stick with it a while!

---

### Post by timcredible on 2009-01-09
1 - if you're building a website, why not use a complete content management system like [joomla]("http://joomla.org") or [drupal]("http://drupal.org")?  they're open source and a thousand times better and easier than any html editor like dreamweaver.  if you're just making a page or two, kompozer is available.

2 - if you don't like gimp, try digikam, it's very good, the only thing that you can't do is select parts of a photo and work on just that part.  and, if you really like photoshop, there's a plugin called gimpshop that changes all the gimp menus to be just like photoshop so it's an easy transition.

3 - use python

4 - let's see, there's quanta, bluefish, and a bunch more that i can't remember right now

---

### Post by Wovaki on 2009-01-09
@namdung
What is FOSS?

I also heard that Mono development was not very good...I don't know because I never tried it though.

I'm just a beginner in programming, I brifly worked with C++ for a little bit in school, but I did not learn anything major. I have been programming in VB.NET for almost a year now, but I don't know if I'm ready for C++, because I heard its a very difficult language.

I was thinking about switching to C# soon because it is close to VB.NET and its supposed to be more powerful, and I thought after I did some C# maybe I would switch to C++.

I have never tried Java.

What about developing for both Windows and Linux, how would I do this once I get programming with Linux?

I have never used WINE before, do I have to install DreamWeaver onto WINE?

@timcredible
How do I get this plugin?
Thanks,
Wovaki

---

### Post by mssever on 2009-01-09
For your programming questions, head over to the Programming Talk subforum and read the stickies there. There's lots of good information, and all the programming questions you asked have been thoroughly answered there.

---

### Post by namdung on 2009-01-09
FLOSS - Free/Libre Open Source Software

Mono is a commendable project on the MS.Net Framework. Don't believe everything u've heard.

I believe language is just a medium to express ur thoughts, if u have any. Likewise, if u have a strong programming/analytical/logical mind migrating from one language to another shouldn't a big issue. If ur concepts of OOPS is strong than migration from VB.NET ==> C#, C++, Java shouldn't be an issue. I'm unsure if there is anything that VB.NET can't do that C# can. 

Don't worry about cross platform software now, as all the above programs can build applications for both Linux and Windows OS. I must say that MS has done a commendable job with the .NET Framework but since I don't trust MS and its policies, I would give others the edge instead of C# or VB.NET.

To install Dreamweaver: First install WINE in Ubuntu and than install the Windows software as u'd do on a Windows machine.

---

### Post by Wovaki on 2009-01-09
> **namdung said:**
> FLOSS - Free/Libre Open Source Software

Mono is a commendable project on the MS.Net Framework. Don't believe everything u've heard.

I believe language is just a medium to express ur thoughts, if u have any. Likewise, if u have a strong programming/analytical/logical mind migrating from one language to another shouldn't a big issue. If ur concepts of OOPS is strong than migration from VB.NET ==> C#, C++, Java shouldn't be an issue. I'm unsure if there is anything that VB.NET can't do that C# can. 

Don't worry about cross platform software now, as all the above programs can build applications for both Linux and Windows OS. I must say that MS has done a commendable job with the .NET Framework but since I don't trust MS and its policies, I would give others the edge instead of C# or VB.NET.

To install Dreamweaver: First install WINE in Ubuntu and than install the Windows software as u'd do on a Windows machine.

Alright thanks!
I will give C++ or Java a try, 1 more question...
Is it easier to program on one OS or the other, regardless of language?
Do you have to do anything different on Linux than you have to do on Windows?

Thanks!

---

### Post by namdung on 2009-01-09
> **Wovaki said:**
> 
Is it easier to program on one OS or the other, regardless of language?
Do you have to do anything different on Linux than you have to do on Windows?

Answer to the above is NO. A program logic/syntax doesn't change with different OS. All the major IDEs (except MS Visual Studio) are available for both platforms. I'm able to run Turbo C++ in Ubuntu using DOSBOX!!!

---

### Post by mssever on 2009-01-09
> **Wovaki said:**
> Alright thanks!
I will give C++ or Java a try, 1 more question...
Is it easier to program on one OS or the other, regardless of language?
Do you have to do anything different on Linux than you have to do on Windows?It depends on the language, tools you're using, and the task you're working on. The biggest change will likely be the GUI toolkit--though it's possible to do that in a cross-platform way, too.

And seriously, give Python a shot.

---

### Post by mssever on 2009-01-09
> **namdung said:**
> Answer to the above is NO. A program logic/syntax doesn't change with different OS. All the major IDEs (except MS Visual Studio) are available for both platforms. I'm able to run Turbo C++ in Ubuntu using DOSBOX!!!
This answer isn't quite true. There are differences, especially cultural differences, that make programming for Windows different than programming Linux. And if you have to jump through hoops to use some Windows IDE in Linux, it might be better to look for a different tool.

---

