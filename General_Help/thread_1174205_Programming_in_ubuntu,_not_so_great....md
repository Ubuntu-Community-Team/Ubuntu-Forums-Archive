---
title: "Programming in ubuntu, not so great..."
date: 2009-05-30
forum: General Help
---

### Post by kmaster228 on 2009-05-30
hi all 
i am dualbooting with windows and on windows i have visual basic 2008 installed and i love it... it powerful, easy and there are plenty of tutorials easily available...
but when using my highly prefered ubuntu i find nothing similar
i tried mono but that could only make programs completely from code  and had no drag n drop interface or even a designer view... and that is quite difficult for em to work with... ive had sevaral problems installing gambas and i have tried this software called basic-256 or something in the repos... none of them are as good as VB.. i mean its doesnt have to be a clone it just has to like it and able to have the same interface...
 im even very willing to learn new programming languages that are easy, powerful have a designer plus coding view...i know that mono has a designer view for C# but its aweful and alot of the tutorials i find for C# are in visual studio and dont work in mono...
every body seems to love python, but personally i hate it.. it comes up in a terminal and thats it....imnot sure how you can even make an application in it all if seen are helloworld apps that just write hello world in the terminal.. and even that takes hordes of code...whereas in VB you just type msgbox (" Helloworld") and you done!
so does any body know any easy to use programming languages with a gui?:popcorn:

---

### Post by directhex on 2009-05-30
Sounds like you want Gambas.

---

### Post by kmaster228 on 2009-05-31
yes but when ever i try to install gambas ffrom the repos it asks me to insert my kubuntu CD... and im using ubuntu... and i also downloaded the file from their website and i followed the instructions, cd to the folder then type ./configure then enter make, then enter make install... the command ran and then nothing

---

### Post by steeleyuk on 2009-05-31
There are many interface designers for Linux, Glade can do GTK apps, Qt Designers can do Qt apps, wxGlade provides for wx widgets. They are just a few of many.

You can also use an IDE such as MonoDevelop, Netbeans or Eclipse to have syntax highlighting and other functions (though I've never used them).

Generally, what you do is type your code in a text editor and make all the connections to the interface. Same applies with Python. You can use the terminal for several languages but primarily you'll want to use either gedit, vim, emacs, nano, kate, whatever...

---

### Post by mcduck on 2009-05-31
> **kmaster228 said:**
> yes but when ever i try to install gambas ffrom the repos it asks me to insert my kubuntu CD... and im using ubuntu... and i also downloaded the file from their website and i followed the instructions, cd to the folder then type ./configure then enter make, then enter make install... the command ran and then nothing

To get rid of the message asking for the CD, go to System/Administration/Software Sources and disale the CD on the Ubuntu Software-tab.

What comes to Visual Basic versus other programming languages, easy isn't the same as powerful. There's a reason why none of the good programs are made with VB.. ;) The default rule is that programming is about coding, not drag&drop.

Should you consider some more powerful programming language Glade is a nice tool for creating graphical user interfaces for your programs and can be used together with C, C++, Java, Perl, Python, C#, Pike, Ruby, Haskell, Objective Caml and Scheme.

---

### Post by kmaster228 on 2009-05-31
thank you... i dont neccesary need VB i just need something like it... i would love to learn python.. but its just doesnt seem promising... im mean i can make a windows by typing in lots of code definging the height n width in pixels, adding color or adjustments by typing in some code i find online in a tutorial or just have a nice interface where you can do exactly the same in minutes... thanks for you suggestion of glade it looks promising and i dont mind learning a new language... i have heard ruby is good as well as c# and perl.. which do you suggest i try, and which is easy? also i want to try out qt do you know any tutorials for any of these programming languages that would be very helpful thank you!

---

### Post by ActiveFrost on 2009-05-31
> which do you suggest i try, and which is easy?
1) Programming language should not be easy ( otherwise we should rename it to "slang", known by everyone & everywhere ).
2) Take a look at Java ;)

---

### Post by s.fox on 2009-05-31
Hi,

If you want to lean perl then I recommend following the tutorials on [this]("http://www.tizag.com/perlT/") site,

-Ash R

---

### Post by 3rdalbum on 2009-05-31
It's not maintained anymore (though it may be coming back under a new name) but I like Pythoncard. Did you try it?

> imnot sure how you can even make an application in it all if seen are helloworld apps that just write hello world in the terminal..and even that takes hordes of code.

You're not confusing Python with Java, are you? To print a line to the terminal in Python, you just do:

```
print "Hello, world"
```

And that's it. If you want a messagebox:

```
import commands
commands.getoutput("""zenity --info --text="Hello, world\!" """)
```

---

### Post by kmaster228 on 2009-05-31
ok so installed glade... now what i manged to place a button that filled the whole window and i am not able to resize it... and i do i start to code? where do i type and how do i compile the program?

---

### Post by Mirge on 2009-05-31
> **kmaster228 said:**
> ok so installed glade... now what i manged to place a button that filled the whole window and i am not able to resize it... and i do i start to code? where do i type and how do i compile the program?

[http://www.google.com/#hl=en&q=glade+tutorial&aq=f&oq=&aqi=g7&=Google+Search&=I%27m+Feeling+Lucky&fp=vBGU4KyIork](http://www.google.com/#hl=en&q=glade+tutorial&aq=f&oq=&aqi=g7&=Google+Search&=I%27m+Feeling+Lucky&fp=vBGU4KyIork)

---

### Post by directhex on 2009-05-31
> **kmaster228 said:**
> ok so installed glade... now what i manged to place a button that filled the whole window and i am not able to resize it... and i do i start to code? where do i type and how do i compile the program?

GTK (Glade) is container-based, not pixel-based. This means that you can't place widgets "exactly" where you want - but you gain other benefits such as your window behaving smoothly if your system font size changes, or you use a right-to-left language. Pixel-based has none of these benefits, which is why pixel-based is dead (i.e. the new Windows GUI system, WPF, is container-based like GTK

To place multiple items, place HBoxes, VBoxes, Tables, and other containers

---

### Post by kmaster228 on 2009-05-31
thanks im looking a tutorial and i looks promising... and do you you know any python tutorials and i also want to know examples of python programs before i start it thank you

---

### Post by kmaster228 on 2009-06-01
Ok sorry i would like to start from the beginning ( or maybe start a new thread ?)

 does any body know a good programming language for a beginner and can you tell me all the resources ( complilers, editors etc. preferably an IDE , tutorials everything) everything i need to get started thank you

---

### Post by directhex on 2009-06-01
> **kmaster228 said:**
> Ok sorry i would like to start from the beginning ( or maybe start a new thread ?)

 does any body know a good programming language for a beginner and can you tell me all the resources ( complilers, editors etc. preferably an IDE , tutorials everything) everything i need to get started thank you

MonoDevelop & C#? ;)

---

### Post by Mirge on 2009-06-01
> **kmaster228 said:**
> Ok sorry i would like to start from the beginning ( or maybe start a new thread ?)

 does any body know a good programming language for a beginner and can you tell me all the resources ( complilers, editors etc. preferably an IDE , tutorials everything) everything i need to get started thank you

One IDE that I particular enjoy using is Geany. I was using Editplus3, but I much prefer Geany even though I can run Editplus just fine using wine.

As far as language, there is a learning curve regardless of what you choose. It's hard to recommend a language without knowing what you plan on doing with it.

---

### Post by ellgor on 2009-06-01
Hi, 

If you are still looking around take a look at kommander, most of the commands are built in but I do recall looking at the forum for the project and own scripts can be used, in fact encouraged as other users might benefit from your input, worth a look.

Regards, Ellgor.

---

### Post by mixmaster on 2009-06-01
"Learning Python" by Mark Lutz (O'Reilly books) is a good starter.

"Programming Python" by the same author/publisher is a much denser work but contains some pretty complete real-world examples.

Bear in mind that GUIs and app-builders are not the only way, or even necessarily the best way, to write code.  You will end up with a much more complete understanding if you start off just using a text editor and a compiler/interpreter.  Later you can use the various tools and frameworks to take the slog out of coding.

---

### Post by ibuclaw on 2009-06-01
I haven't personally tried it, but have heard good things about [gazpacho]("apt:gazpacho"), as people have already said in this thread, Linux GUI programming is **container** based, so don't expect it to be a straightforward drag+drop designer, layout the Containers correctly, then the rest should flow. :)

Regards
Iain

---

### Post by kmaster228 on 2009-06-01
thanks all for your contributions! i have decided to start witing C++ with glade all though the tutorial i am readin upon seem quite complicated, if that doesnt work for me ill try monodevelop with C#

---

### Post by loneowais on 2009-06-01
Just install Glade for Visual Designer.

Learn a bit of Python. 

Learn how to use a Glade file with python.

You'll be making apps within hours.

I'm myself thinking of learning pyGTK soon.

Best of Luck to me and to you too.

---

### Post by Mirge on 2009-06-01
C++ is a good general-purpose language, imo. It will also lay out the foundation for learning other languages quite a bit quicker.

---

### Post by kalaharix on 2009-06-02
Hi

Container based? You mean a bit like using tables to lay out your web-page html. lol.

Gambas can be container-based or pixel-based. Your choice.

rgds

---

### Post by RobOrr on 2009-06-02
Pixel based leads to bloated code if you want the user to be able to use both written languages that read from left to right (like english, most european languages) and languages that read right to left (like arabic, hebrew, etc) as your layout will be the same so you need to essentially code two GUIs.(or at least that was what I found. Better programmers would find a much better way around this I guess) There is a reason MS have switched over to container-based GUIs, and I would compare them to frames of a website, not tables.

---

### Post by kmaster228 on 2009-06-04
ok so all of you say that container based is good and i agree but sometimes it can get iritating when you want a widget to go somewhere but it just wont... and also everyone is saying to try out python...so i guess python + glade it is!

---

