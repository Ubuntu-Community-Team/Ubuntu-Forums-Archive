---
title: "Very Basic Shell Scripting Help"
date: 2009-04-28
forum: General Help
---

### Post by Nir Friedman on 2009-04-28
Hello,
I have a menu driven C++ program that does some numerical simulations. I want to keep doing simulations with different choices of menu options. Of course I could tear up some code and set this up, but this would certainly be more work than just writing a shell script to simulate my input. Is there some way to make the shell script drive the C++ program? I tried as a first attempt

./HysteresisConsole
l 128
run 1

So I run the program, and then I try to set one of the parameters using the syntax of the code. Then I run a simulation. Of course what happens is that its runs the program, waits to exit, when I exit manually it tries to run the other two and throws error messages. So, I need it to run ./HysteresisConsole, wait until ./HysteresisConsole is asking for input and then feed it the input that I want it to. I've also experimented with the piping in command (||) to no success. Help?

---

### Post by mb_webguy on 2009-04-28
> **Nir Friedman said:**
> Hello,
I have a menu driven C++ program that does some numerical simulations. I want to keep doing simulations with different choices of menu options. Of course I could tear up some code and set this up, but this would certainly be more work than just writing a shell script to simulate my input. Is there some way to make the shell script drive the C++ program? I tried as a first attempt

./HysteresisConsole
l 128
run 1

So I run the program, and then I try to set one of the parameters using the syntax of the code. Then I run a simulation. Of course what happens is that its runs the program, waits to exit, when I exit manually it tries to run the other two and throws error messages. So, I need it to run ./HysteresisConsole, wait until ./HysteresisConsole is asking for input and then feed it the input that I want it to. I've also experimented with the piping in command (||) to no success. Help?

If one instance of the program doesn't depend on the previous instance, you can append "&" to the end of the command to make it run in the background.  For example:```
command1 &
command2
```This would allow you to run command2 immediately, without waiting for command1 to finish.

---

### Post by Nir Friedman on 2009-04-28
They're not separate instances of the program. THere's one instance that I'm interested in feeding parameters. When I run ./HysteresisConsole, I get a menu system. One of the commands described there is "enter l # to change dimension". When you enter l 128 it changes the size (for example). I want to run a first command from the bash shell, and then wait until the C++ program is demanding input and feed that program l 128 as text input. When I use & it runs the l 128 as bash which is not what I want.

---

### Post by mb_webguy on 2009-04-28
Ah... that's a bit different.  I thought you were saying you wanted to use the scripts to feed the program different command-line parameters.

I'm not sure how you'd go about doing that.  The script would have to be able to detect somehow that the application was waiting for input.  If the application used basic command prompts, I could probably come up with something, but with a menu I'd have no idea how you'd begin to go about doing what you want.  Sorry.

---

