---
title: "Creating new launcher in Classic Main Menu"
date: 2011-12-19
forum: Desktop Environments
---

### Post by carwe on 2011-12-19
Hi,

I have the Classic Main Menu installed. I'm trying to create a launcher for an application, but I don't get it to work.

I have tried the ideas on this page:
[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

I can start the application with 
sh /opt/ModelSim6.5f/modeltech/bin/vsim
in terminal.

Executing "file /opt/ModelSim6.5f/modeltech/bin/vsim" gives:
/opt/ModelSim6.5f/modeltech/bin/vsim: symbolic link to `../vco'

This is what I have done:
In Preferences->Main Menu, "Properties" for the application reads:
Type: Application in Terminal (tried the other one as well)
Command: sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"

Then when I expand the menu and click the icon, nothing happens.

I also tried creating a script to start it, calling the script as the command. But I don't even manage to start the program by running such a script in Terminal. The script contains the line
sh /opt/ModelSim6.5f/modeltech/vco
...and giving it execute rights and then executing the script with ./<scriptName> just types the word "linux" to the prompt, on a new line, and the program isn't started.

Could anyone help me out?

Thanks,
Carl

---

### Post by jerrrys on 2011-12-20
"The easy way" in your link.  Did you hold down th **Alt** button while right clicking on a blank spot on the panel?

---

### Post by carwe on 2011-12-20
> **jerrrys said:**
> "The easy way" in your link.  Did you hold down th **Alt** button while right clicking on a blank spot on the panel?

Well, I don't wish to create a launcher on a panel, but in the Classic Start Menu.

Those instructions tell how to get up the dialog to create a launcher - I do get it but for the Classic Start Menu, the problem is that although I'm entering what I think I should, the launcher doesn't work...

---

### Post by ubix on 2011-12-20
**Right-click** on _Applications_, and you'll be able to edit Menus

---

### Post by carwe on 2011-12-21
> **ubix said:**
> **Right-click** on _Applications_, and you'll be able to edit Menus

Please read my original post. I do get up the dialogs for adding/editing a launcher. The problem is that there is one specific program I just can't start through a launcher.

---

### Post by jerrrys on 2011-12-21
OK, I understand.  Just don't see how come this is giving you grief.  So I guess I need to load it and find out for myself.  Can you give me that link?

---

### Post by ubix on 2011-12-21
I have no idea what is your problem. Why are you asking for help on Ubuntu forums for some proprietary software which your **»_sh /opt/ModelSim6.5f/modeltech/bin/vsim_«** obviously is?

Here's what I suggest you do if you want to create a louncher, but certainly not one with menu. There is no such thing anyways:

(1) from your Applications menu drag any application icon to the desktop, for example **»Applications->Games->AisleRiot Solitaire«**.
(2) Once it's on the desktop **right-click** it and select _Properties_.

(3) Make sure you are in **Basic** tab. There is an icon of the application which you wish to change.

(4) To change its icon in **Basic** tab double click (left click) the icon. This opens a file navigator window where you should navigate to your desired icon image file and select it. 

I am not sure that is what you want, but it's about all you can do outside of the ***Main Menu*** on the panel or on the panel. You can also drag icons to the panel if you wish. But changing icons there is not possible.


If you insist working with menus, but for some reason do not know how to Right-click the Applications on your panel, you can in your terminal enter the following command manually:

```
/usr/bin/python -OOt /usr/bin/alacarte
```

---

### Post by mcduck on 2011-12-22
> **carwe said:**
> Hi,

I have the Classic Main Menu installed. I'm trying to create a launcher for an application, but I don't get it to work.

I have tried the ideas on this page:
[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

I can start the application with 
sh /opt/ModelSim6.5f/modeltech/bin/vsim
in terminal.

Executing "file /opt/ModelSim6.5f/modeltech/bin/vsim" gives:
/opt/ModelSim6.5f/modeltech/bin/vsim: symbolic link to `../vco'

This is what I have done:
In Preferences->Main Menu, "Properties" for the application reads:
Type: Application in Terminal (tried the other one as well)
Command: sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"

Then when I expand the menu and click the icon, nothing happens.

I also tried creating a script to start it, calling the script as the command. But I don't even manage to start the program by running such a script in Terminal. The script contains the line
sh /opt/ModelSim6.5f/modeltech/vco
...and giving it execute rights and then executing the script with ./<scriptName> just types the word "linux" to the prompt, on a new line, and the program isn't started.

Could anyone help me out?

Thanks,
Carl
The problem isn't that the program wouldn't work, it's just that since you aren't telling the launcher to execute the program in a terminal window, it's simply running the script in background.

Also the problem with the script not executing correctly if you just set it executable and run with ./nameofthescript instead of sh ./nameofthescript would indicate that there is something wrong with the script itself. Make sure it has a shebang on the first line defining the correct shell to be used for the script ("#!/bin/sh", for example).

---

### Post by carwe on 2011-12-22
> **jerrrys said:**
> OK, I understand.  Just don't see how come this is giving you grief.  So I guess I need to load it and find out for myself.  Can you give me that link?

Sorry, what link are you asking for?

Thanks for the help.

---

### Post by ubix on 2011-12-22
sorry

---

### Post by ubix on 2011-12-22
> **mcduck said:**
> The problem isn't that the program wouldn't work, it's just that since you aren't telling the launcher to execute the program in a terminal window, it's simply running the script in background.

Also the problem with the script not executing correctly if you just set it executable and run with ./nameofthescript instead of sh ./nameofthescript would indicate that there is something wrong with the script itself. Make sure it has a shebang on the first line defining the correct shell to be used for the script ("#!/bin/sh", for example).

Shebang is not the problem in this case, because the command is executed with the **»sh«** prefix. Shebang's purpose on Unix / Linux systems is to allow commands, with execution bit set, without prefixing **»sh«**. In other words **»sh«** is used to execute regular files, with error-free scripts as commands, even if these files do not have execute permissions. _Prefixing a command file with **»sh«** obviates the need for shebang!_

---

### Post by ubix on 2011-12-22
***carwe***, I really do not understand your problem. I gave you perfectly workable example how to create a launcher. Perhaps you are missing the point where you use **Preferences** on a launcher you created by dragging an app-icon to the desktop. In the **Preferences** you can change all the text including the command you are executing and indeed the Icon for the Application. So for instance if you drag an application for a game to desktop, you can change it to your needs with an entirely new behaviour (command). Indeed the command has to be a valid GUI application, scripts can not be executed in terminals!  Earlier I only showed you how to change an icon to match your application. An Appropriate icon can be find in the **/usr/share/icons**. Following is a more complete example showing how to make a launcher which runs **/usr/bin/nautilus** (the file navigator) command from the **»AisleRiot Solitaire«** application

> 
(1) from your Applications menu drag **»Applications->Games->AisleRiot Solitaire«** to your desktop.
(2) Once it's on the desktop **right-click** it and select _Properties_.
(3) In the **Basic** tab, change the Name, Description, **_Command_**, and Comment to match new command you are installing (**/usr/bin/nautilus**).  
(4) In the **Basic** tab, change the icon. To change the icon double click (left click) the icon. This opens a file navigator window where you should navigate to your desired icon image file and select it (most likely from **/usr/share/icons**).
(5) On the desktop right-click the newly created launcher and **»Resize Icon ...«** if you so desire.

What is here so hard to understand?

---

### Post by ubix on 2011-12-22
***carwe***, your problem eluded me mostly because of your unfortunate choice of title for this thread. I was convinced you could not create a launcher on the desktop. Indeed, only now it is clear to me that you want the option of ***»_Alt+Right-clicking the panel_->Add to Panel->Cust.-App.-Launcher«***, and that there is a problem for you because your command is incorrect. You should give us much more info about your command, which I noted already looks like some proprietary stuff, that has little if anything to do with Ubuntu. This is also why **jerrrys** is asking you for the link. The culprit here is your ***»_sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"_«***.

You should at least cooperate with us who are trying to help. So tell us what are **vsim, vco** and indeed **ModelSim6.5f**. It would also be appropriate if perhaps you tell us where did these things come from (are they some third party stuff), and most importantly, can you run what you want from a terminal?

---

### Post by mcduck on 2011-12-22
> **ubix said:**
> Shebang is not the problem in this case, because the command is executed with the **»sh«** prefix. Shebang's purpose on Unix / Linux systems is to allow commands, with execution bit set, without prefixing **»sh«**. In other words **»sh«** is used to execute regular files, with error-free scripts as commands, even if these files do not have execute permissions. _Prefixing a command file with **»sh«** obviates the need for shebang!_

If you didn't notice the OP said he has problems when he *doesn't* execute the file with *sh* command.

And also rember that Ubuntu uses two different shells by default, Dash and Bash. That makes it quite important in many cases to pay attention to what commands and features you use in scripts, and which shell is actually used to interpret them.

(Try to run a script with bash-specific features with "sh", or use one as a system script without a correct shebang, and you'll see what I mean. ;))

---

### Post by ubix on 2011-12-22
> **mcduck said:**
> ...
Try to run a script with bash-specific features with "sh", or use one as a system script without a correct shebang, and you'll see what I mean. ;)You are right shebang, if it is different from what is used in configuration of the launcher could be a problem, and that underlines the fact that too little attention and emphasis in this thread is on the command itself. _Nobody insists that the command in question be first run from the terminal_. Only this will convince us the problem really is the command, and only then it would make sense to look into the command, providing those looking are familiar with the script it is written in.

---

### Post by carwe on 2011-12-23
Thank's everyone who are trying to help.

For reasons I can't control, I've been unable to boot Ubuntu for the last two days. Which is the reason I haven't replied to some of the suggestions in this thread yet. I hope I can boot it soon, but here are the replys I can give right now, without being able to test things in Ubuntu.

Ubix, thanks for the detailed instructions on how to create a launcher by dragging an icon from a menu and all that, but this has nothing to do with my problem. Judging from your last reply I guesse you understand that by now.

To be clear what I want to do:
So, I'm running Ubuntu 11.10 with Unity and I have installed Classical Main Menu. It's sitting in the top panel, but isn't called "Applications" like the old one, it just has the "Ubuntu wheel" icon. I wish to add an application, ModelSim, to one of the sub-menus of that menu. ModelSim is installed and I can start it from the terminal with the command described in my original post.

I have added installed applications to the menu successfully before.

I might be mis-using the term "Launcher". Maybe it's only used for starting an application from an icon on the desktop or on a panel, not from within Classical Start Menu. However, editing a menu item for Classical Main Menu brings up the same dialog as that for creating a launcher on a panel.

I do know how to add the item itself to the menu. The problem is that when I have don that and click the icon in the menu, nothing happens - ModelSim won't start, as I had expected.

Having read my original post and with the link I provided, I can't see how it's unclear what I want to do and what doesn't work, but I'm sorry if I wasn't clear enough.

> **ubix said:**
> carwe, your problem eluded me mostly because of your unfortunate choice of title for this thread. I was convinced you could not create a launcher on the desktop.

OK, don't really understand how the title "Creating new launcher in Classic Main Menu" made you think that. Especially since I've stated clearly what I have typed into the fields of "Create Launcher" dialog in my OP it should be obvious that I got that far.

> **ubix said:**
> Indeed, only now it is clear to me that you want the option of »Alt+Right-clicking the panel->Add to Panel->Cust.-App.-Launcher«,

Almost, I want to create a launcher inside of Classical Main Menu, but it should be the same as creating a launcher on a panel since the dialogs look the same.

> **ubix said:**
> and that there is a problem for you because your command is incorrect.

Yes, I believe and always have believed that to be the problem too.

> **ubix said:**
> You should give us much more info about your command, which I noted already looks like some proprietary stuff, [...] So tell us what are vsim, vco and indeed ModelSim6.5f.

Yes, it's a 3rd party proprietary application. I gave the output of executing "file vsim" in my original post. Since I can start the application in the terminal with "sh /opt/ModelSim6.5f/modeltech/bin/vsim" I thought that information would be enough. I'll check what "vco" is as soon that I can boot Ubuntu, but I believe it is a script which starts the application.

> **ubix said:**
> and most importantly, can you run what you want from a terminal?

As stated in my OP I can, there is also the command to start it written-out.

> **ubix said:**
> I have no idea what is your problem. Why are you  asking for help on Ubuntu forums for some proprietary software which  your »sh /opt/ModelSim6.5f/modeltech/bin/vsim« obviously is?

I can start the application from the terminal, but don't manage to start  it through a menu item/launcher. Hence there is no problem with the program  itself, the question is how I can start it through a menu. I guesse that  would be a typical question to ask in a Ubuntu forum.




Some comments on older replies just to be clear, although the above information has probably sorted this out already:

> **ubix said:**
> Right-click on Applications, and you'll be able to edit Menus

I can and always have been able to edit the menu and add menu items (however for Classical Main Menu, it can't be done in thet way).

> **mcduck said:**
> The problem isn't that the program wouldn't work, it's just that since you aren't telling the launcher to execute the program in a terminal window, it's simply running the script in background.

I tried to select both "Application in Terminal" and the other option, as stated in my original post. None of them works.

---

### Post by ubix on 2011-12-23
***carwe***, sorry I only skimmed through your last reply (don't have time now) but it looks that you are not logged into ***»GNOME Classic«*** at all. If you were you would see Applications on top left in the panel. However, what puzzles me is that you are able to come into the launcher window. Can you please explain how do you start it (the launcher window namely), since ***»Alt+Right-clicking the panel«*** does not work, where I believe you are, namely, in Unity? 

To get into  ***»GNOME Classic«*** you have to ***»Log Out ...«*** by clicking the ***»Shut Down«*** icon on the extreme right of the panel and select there the option ***»Log Out ...«***. This will bring you to the *»Guest Session«* _login screen_ where you enter your password. But before you enter the password or press <Enter> for the password you must click on the little ***»cog-wheel«*** icon, and select ***»_GNOME Classic_«*** or ***»_GNOME Classic (No effects)_«***. Next, completing the password entry will only start the ***»GNOME Classic«*** (you can get back to Unity the same way, indeed choosing Unity instead).  You should see now Applications on the top left side of the panel. On the panel you can  ***»_Alt+Right-click_«*** either on Applications or right of it on empty space on the panel. The two clicks perform different actions! First works with menus second works with panel itself. You want the latter.

Once you will have this right, return to our previous discussion. The best place to start is with: ***»_Alt+Right-click the panel_->Add to Panel->Cust.-App.-Launcher«***. I believe you will have no trouble accomplishing what you want, unless your application is not a GUI one and runs from a terminal.

---

### Post by carwe on 2011-12-24
> **ubix said:**
> ***carwe***, sorry I only skimmed through your last reply (don't have time now) but it looks that you are not logged into ***»GNOME Classic«*** at all. If you were you would see 
[...]



ubix, I'm thankful you're willing to help, but you don't accomplish it in this way. You need to read my last reply carefully, you write that you only skimmed it through. So wait until you have the time and read it through carefully.

Nothing of what you write in this reply has anything to do with my problem what so ever.

---

### Post by ubix on 2011-12-24
We clearly have a communications problem. Your posts are too vague and you are using some misleading terminology the most damaging of all is your persistent use of the name (noun) of the window called *"Create Launcher"* sometimes using is as a predicate, for instance, as in your statement ***»_I want to create a launcher inside of Classical Main Menu_«***. The correct thing to say here would be: ***»I want to ad another item to my menu in ... or under ...«*** (where the dots indicate a subsection, which in your case is "Other".

Couple the above poor choice of terminology with your erroneous use of words like  ***»_Preferences_«*** in the following example, where there is no word or item called *Preferences* in which you located *»Main Menu«* and then on top of that _incorrectly selected ***»Properties«*** on the ***»Main Menu«***_. All this confusion is found in your following statement 

> **carwe said:**
> ...
This is what I have done:
In Preferences->Main Menu, "Properties" for the application reads:
Type: Application in Terminal (tried the other one as well)
Command: sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"

Then when I expand the menu and click the icon, nothing happens.
...


This would more correctly but logically still blissfully wrong be written as:  
/NOTE: here European quotes (**»«**) indicate the corrections/

> **carwe said:**
> ...
This is what I have done:
In ***»_"Other"_«***->Main Menu, *»_"Properties"_«* for the application reads:
Type: Application in Terminal (tried the other one as well)
Command: sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"
...

Here you made two mistakes in the same statement. The first is replacing the word ***»_"Other"_«*** with the non-existent ***»"Preferences"«***, which let me to believe that you are not in the same GUI as you believe. And the second is the fact that you do not understand how the *»Edit Menus«* facility works (which BTW for you is the same as *»Main Menu«* //very confusing). One can conclude this from your use of the button named _***Properties***_ on  the ***»_Main Menu_«*** item within the ***»_Main Menu_«** editing facility*.

This is the correct wording as well as the procedure you need to do:

```

1) Right Click the ***»Main Menu (Ubuntu icon)«*** on the Panel.
2) Select Edit Menus 
      ... Main Menu editing window appears
      
3) Under column "Menus:" highlight Other
4) Click button "New Item"
      ... Create Launcher appears
5) In "Type" select "Application in Terminal"
6) Enter its name (Vsim)
7) Enter the command (sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim")
8) Optionally enter Comment
9) Optionally change the icon by clicking the icon 
10) Click OK button

```

I hope this will now work for you.

---

### Post by carwe on 2011-12-25
I can now boot Ubuntu again, here are some updates:

- "vco": "vco" is a script file, which runs a lot of script commands and finally starts the GUI.

- I tried adding #!/bin/bash at the first line of my scipt file - didn't help.

I changed my custom start script to contain the line
/opt/ModelSim6.5f/modeltech/bin/vsim
...and running the script from Terminal now starts the application correctly (with or without !#/bin/bash on the first line).

So I tried calling this script from my launcher, but still, when I click the launcher, nothing happens. I tried both "Application"/"Application in terminal" as "Type", and for command, I tried "./scriptname", "sh -c scriptname", "/opt/ModelSim6.5f/modeltech/bin/vsim", "sh -c /opt/ModelSim6.5f/modeltech/bin/vsim" and and many others, and for all of them both alternatives for "Type", and for all those combinations, both with and without shebang as the first line of my script file.

Any ideas anyone? I now have a script that starts the application from Terminal. But I just don't manage to enter the right command to start the application or run the script from my launcher.

---

### Post by carwe on 2011-12-25
> **ubix said:**
> We clearly have a communications problem. Your posts are too vague and you are using some misleading terminology the most damaging of all is your persistent use of the name (noun) of the window called "Create Launcher" sometimes using is as a predicate, for instance, as in your statement »I want to create a launcher inside of Classical Main Menu«. The correct thing to say here would be: »I want to ad another item to my menu in ... or under ...« (where the dots indicate a subsection, which in your case is "Other". 
 
 
In that sentence of mine, I don't intend any reference to any window named "Create launcher". I mean exactly what I write. It is possible though that "I want to create a launcher in Classic Main Menu." would be more gramatically correct. 
 
Your confusion could partly come from you not understanding that I have installed an external program, which brings up the "old" Main Menu in Ubuntu 11.10 with Unity (as I have described). I have referred to it as "Classic Main Menu" since that's what it was called on the page with the instructions I followed to install it. 
 
However, this has nothing to do with my problem. My problem is to get a new launcher to launch my application - regardless of if I place this launcher in this menu, on the desktop or on a panel. I don't know how I can make you understand that there isn't any problem for me to create the launcher itself (to get to the "Launcher properties" window, with "Type", "Name", "Command" etc.). Instead, my problem is that the launcher I create doesn't start the application - there must be someting wrong with the command.

All of your corrections that make out the rest of your reply are wrong. There's a screenshot further down. 

> **ubix said:**
> Couple the above poor choice of terminology with your erroneous use of words like »Preferences« in the following example, where there is no word or item called Preferences 

Oh yes there is.

> **ubix said:**
> in which you located »Main Menu« and then on top of that incorrectly selected »Properties« on the »Main Menu«.

I located Main Menu, starting the Main Menu window, from there I selected "Properties", yes.

> **ubix said:**
> All this confusion is found in your following statement 

[Originally posted by carwe:]
This is what I have done:
In Preferences->Main Menu, "Properties" for the application reads:
Type: Application in Terminal (tried the other one as well)
Command: sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim" 

[Originally posted by ubix:]
 
Here you made two mistakes in the same statement.

Oh no I didn't.

My statements quoted above from my original post are correct down to every letter.

(They are not only for my screenshot below, but also if you're e.g. using the Main Menu with GNOME Desktop.)

 
 [IMG]http://tinypic.com/r/2z6cnyp/5[/IMG][IMG]http://oi39.tinypic.com/2z6cnyp.jpg[/IMG]
 

Starting now, I suggest that we use this thread to make posts that have to do with finding the right command for the launcher to start the application.

---

### Post by ubix on 2011-12-26
> **carwe said:**
> ...
Oh no I didn't.

My statements quoted above from my original post are correct down to every letter.

(They are not only for my screenshot below, but also if you're e.g. using the Main Menu with GNOME Desktop.)
...


Oh, yes you did! Depending on how much you really care to be clear and how much effort you put into understanding of what is being said. I am amazed that you did not see we were talking a about two different environments, which on top of that could have also been customized to the point that they are not recognizable. Your picture has cleared this out, though you could have told us which release you were running! 

The trouble is you are talking about Ubuntu 11.04 whereas I was looking at 11.10. I was misled by ***mcduck's*** info under his nick, where ***»Ubuntu 11.10 Oneiric Ocelot«*** is listed. Regardless of these minor problems caused by the differences in our respective GUIs, you should be able to get the launcher going, unless there is a bug in 10.04, or whatever you are using. In ***»Ubuntu 11.10 Oneiric Ocelot«*** there are no problems and it works as it should.

Here is how this stuff looks on 11.10:


[IMG]http://media10.dropshots.com/photos/967413/20111226/b_001936.jpg[/IMG]

You can see here we both were right

---

### Post by ubix on 2011-12-26
> **carwe said:**
> ...
Starting now, I suggest that we use this thread to make posts that have to do with finding the right command for the launcher to start the application.
As far as I am concerned, this thread can be marked solved, namely in both these environments the launcher is defined in very much the same way, the differences are only in the myriad of ways one can get to the ***»Main Menu editing window«***, which for any "Ubuntu literate" user should be a piece of cake. The core of the instructions I posted earlier remain virtually unchanged:

```

1) Get to the "Main Menu editing window"
2) Under column "Menus:" highlight Other
3) Click button "New Item"
      ... Create Launcher appears
4) In "Type" select "Application in Terminal"
5) Enter its name (Vsim)
6) Enter the command (sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim")
7) Optionally enter Comment
8) Optionally change the icon by clicking the icon 
9) Click OK button

```

***carwe***, from the image you posted is evident that your original post reveals that you do not understand well enough the procedures of creating a new item in the Main Menu hierarchies. You may have created a problem when forcing to modify the "Main Menu item" by clicking »_Properties_« on it rather than merely selecting it, or some other subsection, into which you intend to _add a new Item_ by clicking  ***»New Item«***. (see ***»_... Create Launcher appears_«*** in the instructions above. Unless there is a bug in your release of these desktop features, incorrect use of »_Properties_« on existing items in your menu may have been your only problem.

If you insist on testing a command then I suggest that you first try to add something that we all can do, say add a nautilus command to some section in your menu hierarchy, once you'll succeed in doing that you know there is no bug at least for the Type **»Application«**. To test that there is no bug for Type **»Application in Terminal«** do the following:

(I)

```
echo 'echo "Hello, from terminal"' > /tmp/my_test
sleep 5" >> /tmp/my_test
```
Pay attention to redirection signs **>** and **>>** !!!!



(II)

Next create a launcher for this command as follows:
```

1) Get to the "Main Menu editing window"
2) Under column "Menus:" highlight Other
3) Click button "New Item"
      ... Create Launcher appears
4) In "Type" select "Application in Terminal"
5) Enter its name as it should appear in the section Other, for instance (MyTest)
6) Enter the command (sh /tmp/my_test)
7) test the new item MyTest in your menu

```

No shebangs and no file permissions need to be added or fixed, as long as you do exactly as instructed all should work just fine! The message ***»Hello, from terminal«*** should appear in a terminal for 5 seconds and after that the terminal window will disappear.

---

### Post by ubix on 2011-12-26
> **mcduck said:**
> ...
(Try to run a script with bash-specific features with "sh", or use one as a system script without a correct shebang, and you'll see what I mean. ;))The above instructions ***(I) & (II)*** how to test ***carwe's*** command as shell script clearly show what I meant when I said that sh obviates the need for shebang for any script interpreter. ***»sh«*** just happens to be the  *»Bourne shell interpreter«*. Indeed if the command is written in any other scripting language its interpreter has to be specified instead (usually with the full path), for instance **/bin/bash, /usr/bin/python, /usr/bin/ruby, ...**

---

### Post by carwe on 2011-12-27
> **ubix said:**
> Oh, yes you did! Depending on how much you really care to be clear and how much effort you put into understanding of what is being said. I am amazed that you did not see we were talking a about two different environments, which on top of that could have also been customized to the point that they are not recognizable. Your picture has cleared this out, though you could have told us which release you were running!

The trouble is you are talking about Ubuntu 11.04 whereas I was looking at 11.10. I was misled by mcduck's info under his nick, where »Ubuntu 11.10 Oneiric Ocelot« is listed. Regardless of these minor problems caused by the differences in our respective GUIs, you should be able to get the launcher going, unless there is a bug in 10.04, or whatever you are using. In »Ubuntu 11.10 Oneiric Ocelot« there are no problems and it works as it should.

Here is how this stuff looks on 11.10:

You can see here we both were right

But I have written what release I'm running. And it's still 11.10 (with Unity), not 11.04 which you now seem to think.

My Main Menu doesn't look like yours (no surprise - there are several ways to get the Main Menu into Ubuntu 11.10 with Unity) which you now seem to understand. I've written what actions I've taken with my menu to get to Create Launcher/Edit Launcher windows. For some reason you have kept on complaining about me giving erraneous information just because it doesn't match how it looks on your system. I've been trying to tell you from the start that this doesn't matter since it's not about how to bring up the "Create Launcher" or "Launcher Properties" windows (the same thing, just different title if you create a new item or edit one) -rather, my problem must have something to do with the command.

> **ubix said:**
> carwe, from the image you posted is evident that your original post reveals that you do not understand well enough the procedures of creating a new item in the Main Menu hierarchies.


No no, my original post describes exactly what I'm doing in the screenshot, which is also the way it should be done (the only way it can be done) with the Main Menu on my system. You keep mis-understanding things:

> **ubix said:**
> You may have created a problem when forcing to modify the "Main Menu item" by clicking »Properties« on it rather than merely selecting it, or some other subsection, into which you intend to add a new Item by clicking »New Item«. (see »... Create Launcher appears« in the instructions above. Unless there is a bug in your release of these desktop features, incorrect use of »Properties« on existing items in your menu may have been your only problem.


I haven't changed the properties for the menu item "Main Menu". I've clicked "Main Menu", thereafter selected the ModelSim in the list and then clicked on the button "Properties".

---

### Post by carwe on 2011-12-27
> **ubix said:**
> If you insist on testing a command then I suggest that you first try to add something that we all can do, say add a nautilus command to some section in your menu hierarchy, once you'll succeed in doing that you know there is no bug at least for the Type »Application«.

As I've previously written, I've done that - I have created launchers for other graphical applications than ModelSim and they are working fine and do launch the application when I click the menu item/laucher.

> **ubix said:**
> To test that there is no bug for Type »Application in Terminal«

Good idea. However I believe you mis-typed the code a bit, I guesse you want my_file to read:

```

echo "Hello"
sleep 3

```I created such a file, and then created a launcher with the command you gave. When I click the menu item, a terminal window opens, but nothing more happens - no text is written to the terminal. (The opened terminal has "$" as prompt - my ordinary prompt also shows some other info.)

(I also did try this by adding execute permissions to the file and using shebang as the first line, same results.)

Any idea where we go from here?

---

### Post by carwe on 2011-12-27
I wanted to create a launcher outside the menu, just to test that. I did like this:

[http://shuffleos.com/3274/how-to-create-desktop-launchers-in-ubuntu-11-10-oneiric-ocelot/](http://shuffleos.com/3274/how-to-create-desktop-launchers-in-ubuntu-11-10-oneiric-ocelot/)

...and after having created a launcher on the desktop for my_test, the script runs fine when double-clicking the icon (the text shows as expected in the terminal). So there seem to be some problem about "Applications in terminals", that is specific to placing the launcher in the menu (could be a bug in the menu application).

I also tried to create a launcher for ModelSim on the desktop, using 

```
sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"
```as command (and some other similar commands) but with no luck - nothing happens when I double-click that launcher on the desktop.

---

### Post by ubix on 2011-12-28
> **carwe said:**
> ... However I believe you mis-typed the code a bit, I guesse you want my_file to read ...
...
Any idea where we go from here?

I did not mistype anything, you did! Check your **»my_file«** with **»cat /tmp/my_file«** and you'll see you are missing the _echo_ statement in it! And what the h* is the difference with my and your echo statement, except your typing it in your own way. If you had just cut-n-past'ed my *»Hello, from terminal«* code segment into the terminal _and press enter after that_, it'd create the proper **»my_file«** for you without any errors. I said: ***»_as long as you do exactly as instructed all should work just fine_«***! Do not be inventive where inventiveness is not required, you only added errors into our procedure by trying it your own way.

So you know where you should go from here: try to do exactly what I said you should do, and do not mistype the statements especially all the quotes and **" > "** and **" >> "** redirection signs! 

And stop fiddling with your **»sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"«** before you do not get the two line script I gave you to work!

---

### Post by carwe on 2011-12-28
> **ubix said:**
> I did not mistype anything, you did! Check your »my_file« with »cat /tmp/my_file« and you'll see you are missing the echo statement in it! And what the h* is the difference with my and your echo statement, except your typing it in your own way. If you had just cut-n-past'ed my »Hello, from terminal« code segment into the terminal and press enter after that, it'd create the proper »my_file« for you without any errors. I said: »as long as you do exactly as instructed all should work just fine«! Do not be inventive where inventiveness is not required, you only added errors into our procedure by trying it your own way.

So you know where you should go from here: try to do exactly what I said you should do, and do not mistype the statements especially all the quotes and " > " and " >> " redirection signs!

And stop fiddling with your »sh -c "/opt/ModelSim6.5f/modeltech/bin/vsim"« before you do not get the two line script I gave you to work!


Well, under (I) above in the reply where you gave me the code to create my_test, you told me to type the following two lines into the terminal:

```

echo 'echo "Hello, from terminal"' > /tmp/my_test
sleep 5" >> /tmp/my_test

```...so there is a mis-type on that second line, as I'm sure you can see, that line can't be executed. But (I believe) I understood what you intended and did that - resulting in a my_test file with the two lines I wrote out in my previous reply, and they still read:

```

echo "Hello"
sleep 3

```...that's what e.g. 'cat my_file' provides as output. I believe that's what you intend it to be.



This communication with you has taken hours of my time, surely of yours as well, due to your constant mistakes and mis-understandings. So let's end our correspondance in this thread here and now, I don't see how it could lead to anything else than taking up time for both of us. Your initial motivation was surely to help me out with this, which I am of course still thankful for though. (Of course you, just like anybody else, can still contribute to the thread if you wish, but I will probably not involve myself in any continuation of our discussions since they seem to lead nowhere but rather just take up my time when I have to oppose your blames and mis-understandings.)



Any one else have any ideas on this un-resolved matter? I'm still unable to create a launcher on the desktop that will launch my application.

---

### Post by ubix on 2011-12-28
Sorry my fault, I did "mistype" after all! What I meant should have been: 

```

echo 'echo "Hello, from terminal"' > /tmp/my_test
echo "sleep 5" >> /tmp/my_test

```

You should cut-n-paste or enter exactly these lines in or onto the terminal in your home directory. This is equivalent of creating the **/tmp/my_test** file with the contents

```

echo "Hello, from terminal"
sleep 5

```



It is sensible to test this file actually works by running it from the terminal, by executing the following line _from your home directory_ (of course from terminal):

```

sh /tmp/my_test

```

If it works then you should create your menu item exactly as explained under (II) earlier, which for your convenience I repeat here:

(II)
Next create a launcher for this command as follows:
```

1) Get to the "Main Menu editing window"
2) Under column "Menus:" highlight Other
3) Click button "New Item"
      ... Create Launcher appears
4) In "Type" select "Application in Terminal"
5) Enter its name as it should appear in the section Other, for instance (MyTest)
6) Enter the command (sh /tmp/my_test)
7) test the new item MyTest in your menu

```

I apologize for saying ***»_I did not mistype_«***. Namely, I successfully tested all I wrote on my system, and cutting-n-pasting I must have accidentally skipped the »**echo "**« part.

---

