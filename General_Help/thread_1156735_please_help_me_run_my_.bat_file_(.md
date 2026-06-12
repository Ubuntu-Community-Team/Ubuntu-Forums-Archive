---
title: "please help me run my .bat file :("
date: 2009-05-12
forum: General Help
---

### Post by i rofl i on 2009-05-12
ok, ive got linux ubuntu recently as you can see, and i love it so far...
theres just one problem.
i really want to geet my .bat file up, and it just appears with some code.
i dont know how to convert this into anything i could use either, im hoping  somebody can help me!
here is the code


start javaw -cp Bot;rs.jar;svnkit.jar -Xmx256m com.speljohan.rsbot.Application GUIController members




please i would   be very greatful if somebody could help me, or convert this for me!

---

### Post by pbpersson on 2009-05-12
I have good news and bad news.

First, the bad news - a .bat file is a DOS batch file and you don't really want to run that in a Linux environment.

Now for the good news.  It appears you are attempting to execute .jar files which are Java application files and those are platform independent and should work in the Linux environment.

The Linux counterpart to a batch file is a shell script.

[Here is a thread which discusses a similar problem]("http://ubuntuforums.org/showthread.php?t=1136570"), it might provide some clues for yourself or for someone who can help.

---

### Post by ArtemZ on 2009-05-12
It's looking like you're trying to launch some java application by this command. To get it works in ubuntu you should firstly install java, then try to launch svnkit.jar from command line:
 java -cp Bot;rs.jar;svnkit.jar -Xmx256m com.speljohan.rsbot.Application GUIController members
This command should be executed from the place where your file svnkit.jar located is. Also, I'm not sure that you should use "java" instead of "javaw" in linux, anyway you may try both variants.
If this will works nice, you may create .sh file (analog of .bat) and put in this file something like that:
#!/bin/sh
java -cp Bot;rs.jar;svnkit.jar -Xmx256m com.speljohan.rsbot.Application GUIController members
Dont forgot to chmod this file to 755. If this command is correct and if you will have java correctly installed you will be able to use this file same to your previous .bat.

P.S Sorry for my english, I'm from Russia

---

### Post by i rofl i on 2009-05-12
thanks so far guys, but im still very confused about how im going to do this, as i say.. im very new to ubuntu

---

### Post by i rofl i on 2009-05-12
i have to go to school now, but please please please keep posting suggestions, i will read and reply when i am home, thanks guys for your efforts

---

### Post by lisati on 2009-05-12
> **i rofl i said:**
> thanks so far guys, but im still very confused about how im going to do this, as i say.. im very new to ubuntu

OK, I'm going to expand on ArtemZ's advice here.

[LIST=1]
[*]Go to a terminal (from the Applications->accesories->terminal menu item), and type in the following:
```
gedit myfile.sh
```
This will open up an editor for a new file - "myfile" here is just an example. 

[*]In the editor, type in the following:
```
#!/bin/sh
java -cp Bot;rs.jar;svnkit.jar -Xmx256m com.speljohan.rsbot.Application GUIController members
```
[*]Save the file and close the editor
[*]At the command line, type in the following:
```
chmod myfile.sh 755

```
This will do the "chmod" thing. Again "myfile" is just an example.

[*]At the terminal type in ```
./myfile.sh
```
This will run the file.
[/LIST]

Good luck.

---

### Post by ArtemZ on 2009-05-12
Have you java installed? If no or if you not sure try to check that in Add \ Remove Applications (find Sun Java 6 Runtime)

---

### Post by i rofl i on 2009-05-12
so after text editing do i save as a .sh? or just save it nomally?

---

### Post by lisati on 2009-05-12
> **i rofl i said:**
> so after text editing do i save as a .sh? or just save it nomally?

The ".sh" helps identify it as a **sh**ell script. Beyond that, I'll defer to the advice of people more experienced with scripting...

---

### Post by i rofl i on 2009-05-12
lisat

i tried that, and this came up.

tomg@tomg-laptop:~$ gedit rsbot members
tomg@tomg-laptop:~$ chmod rsbot members.sh 755
try `chmod --help` for more information
tomg@tomg-laptop:~$./rsbot members.sh
bash:  ./rsbot: no such file or directory
tomg@tomg-laptop:~$
tomg@tomg-laptop:~$
tomg@tomg-laptop:~$





p.s is there A faster way to copy and paste terminals? i hd to copy tht down

---

### Post by ArtemZ on 2009-05-12
You are doing it wrong :)
touch members.sh (it's will create members.sh file. you may skip this step if you already have it. check with "ls -a | grep members.sh")
gedit members.sh (just put the folliwing:
```
#!/bin/sh
java -cp Bot;rs.jar;svnkit.jar -Xmx256m com.speljohan.rsbot.Application GUIController members)

```
chmod 755 members.sh (it's will give execution rights to your scripts. But you may skip it if you dont want to launch your script by another programm, e.g cron)
./members.sh (or "sh members.sh" if you havnt chmod it)
Check the output and post it there

---

### Post by Nathan_M on 2009-05-12
> **i rofl i said:**
> lisat

i tried that, and this came up.

tomg@tomg-laptop:~$ gedit rsbot members
tomg@tomg-laptop:~$ chmod rsbot members.sh 755
try `chmod --help` for more information
tomg@tomg-laptop:~$./rsbot members.sh
bash:  ./rsbot: no such file or directory
tomg@tomg-laptop:~$
tomg@tomg-laptop:~$
tomg@tomg-laptop:~$





p.s is there A faster way to copy and paste terminals? i hd to copy tht down

Try it like this:

tomg@tomg-laptop:~$ gedit "rsbot members.sh"
tomg@tomg-laptop:~$ chmod "rsbot members.sh" +x
tomg@tomg-laptop:~$./"rsbot members.sh"

The first command opens the file "rsbot members.sh" using the program gedit, which is a bit like Windows' notepad. If the file "rsbot members.sh" doesn't exist, gedit will create it for you. You then edit the file as other people have instructed, save and close. Closing gedit takes you back to the terminal. The second line changes the permissions on the file to make it executable (able to run as a program). I like to use +x (add executable permission), but others have suggested 755. They both do the same job, but +x might be a bit easier for you to understand. The third line runs the program. You need a ./ before the program to tell the computer that it's in the current directory, and not a shortcut to a program somewhere else. Note that in every line, you need quotes around the file name because it has spaces in it.

---

### Post by Nathan_M on 2009-05-12
Oh, you can do all of this graphically as well, instead of typing in the terminal. Click "Places" > "Home Folder". Right-click in any blank space, and go to "Create Document" > "Empty File". Type the name (rsbot members.sh) and press return. Double-click the file to open it in gedit, and add the text that others have suggested. Close gedit, and right-click the file, and choose Properties. In the permissions tab, check the box that says "Allow executing file as program". Click close. Now double-click the file to run it. If prompted, click "Run in terminal".

---

### Post by i rofl i on 2009-05-12
tomg@tomg-laptop:~$ #!/bin/sh
tomg@tomg-laptop:~$ java -cp Bot;rs.jar;svnkit.jar -Xmx256m com.speljohan.rsbot.Application GUIController members)
bash: syntax error near unexpected token `)'
tomg@tomg-laptop:~$ #!/bin/sh
tomg@tomg-laptop:~$ 


-reply to post at the top of the screen-

the following above happens, any suggestions?

edit. can anybody tell me how to add a screenshot please?
and is temveiwer available for ubuntu? if so it would help very much if somebody could team veiw help me :/ if tahts to much to ask please ignore my question

---

### Post by tbullock on 2009-05-12
To get a screen shot simply hit the print screen button and it should ask you how you want to save it and what you want to do with it. It is fairly simple or was on my computer. And you should be able to copy and paste from the terminal by highlighting and then right click and choose copy. Right click and choose paste. Or that is how mine has been working. I guess it may depend on your version but it worked this way for me on intrepid and jaunty with a Dell laptop.

---

### Post by tbullock on 2009-05-12
Oh yeah, sorry about not helping with the .bat file thing. I can only help with simple stuff like before. I am new to this OS also. Everything I have picked up though has came from this site or works similar to how it does in windows enough that I picked it up. Are you coming from windows I assume?

---

### Post by pbpersson on 2009-05-12
> **i rofl i said:**
> tomg@tomg-laptop:~$ #!/bin/sh
tomg@tomg-laptop:~$ java -cp Bot;rs.jar;svnkit.jar -Xmx256m com.speljohan.rsbot.Application GUIController members)
bash: syntax error near unexpected token `)'


If I were you, I would try taking the right parenthesis away and see what happens

---

### Post by scottuss on 2009-05-12
Welcome to using Ubuntu! :D

Good luck with getting your Java thing running, hope you enjoy using your new OS.

BTW, stick with it. I know it's weird coming from Windows, but hold in there are you'll really feel the benefits!

:guitar:

---

### Post by i rofl i on 2009-05-13
pbp, I don't understand what you mean, could you explain that in more detail please?

---

### Post by dmizer on 2009-05-13
Closed for review. I believe rsbot is a cheating script for Runescape.

---

