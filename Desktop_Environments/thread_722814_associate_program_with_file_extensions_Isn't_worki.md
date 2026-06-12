---
title: "associate program with file extensions Isn't working."
date: 2008-03-12
forum: Desktop Environments
---

### Post by JuinTreize on 2008-03-12
I am new to Linux  and not very tech savvy despite being a second semester programing student.  I am using Feisty Fawn. 
 
I would like to have the option to open text files with my choice of text editors.  I have tried using the file browser -> right click on file -> properties -> open with ->add.  The only programs which show up as options are Firefox and TextEditor.  

One of the programs I would like to add is Notepad++, which I have been running under wine.  The other is emacs (command line version.)  The extensions I want to associate are : .cpp, .h , etc.

I have searched for answers to other similar posts in this forum, the directions given exactly match what I have already tried.

I appreciate anyone who takes the time to help. 

Thanks, 
Juin

---

### Post by scragar on 2008-03-12
just use the right file path and the wine extention IE:
```
wine C:\\programs\\notepad++.exe
```
ofcourse I'm just guessing as to the notepad ++ path(I don't know if you need to use \\ or just \, a normal \ in a terminal would cause unexpected behaviour, so I'm guessing doubling them is right.

---

### Post by JuinTreize on 2008-03-12
Thanks for the lightning fast reply! 
 
I am really a computer& linux newbie, so thanks for bearing with me.  I see that you can use a "custom command " to open files.  I used slocate to find Notepad's path which is
/home/my_name/.wine/drive_c/Program Files/Notepad++/notepad++.exe.   So I just pasted this line into the custom command field.  Now I get the option of opening  a  .h file with Notepad, but nothing happens when I try.  Is there something I'm missing?

BTW, Notepad++ opens files in my home directory as if they were in Z:  . 
Slocate Z:  turns up three listings : /home/my_name/.wine/dosdevices/z: .
                                                              /home/my_name/.ies4linux/ie6/dosdevices/z:
                                                             /home/my_name/.cxoffice/win98/dosdevices/z:

I am not using crossover office (cxoffice), but have been unable to completely uninstall it. 


Juin

---

### Post by scragar on 2008-03-12
try:
```
wine "C:\\Program Files\\Notepad++\\notepad++.exe"
```or:
```
wine "/home/**my_name**/.wine/drive_c/Program Files/Notepad++/notepad++.exe"
```one of them should work.

---

### Post by JuinTreize on 2008-03-12
This was the command  that worked - so close to your original reply.  
wine "C:\\Program Files\\Notepad++\\notepad++.exe"

Thanks a lot, it feels great to have a little assist from a real person.  I am happy with Linux, but have had so many frustrations, big and small in the process of becoming a Linux user.  I feel encouraged  that the Linux community I've heard about might actually exist, and welcome a newcomer who does not yet speak the language.

thank you posted -  I' m very pleased.

juin

---

