---
title: "STEPMANIA on 12.04LTS INSTALLATION GUIDE NO BAD PPA"
date: 2013-04-24
forum: Gaming &amp; Leisure
---

### Post by FenrirXIII on 2013-04-24
How to install Stepmania in Ubuntu 12.04 LTS
 

 Turn your computer into a dance machine. Great for working out and unwinding.
 

 REQUIRES 7zip program (found in Ubuntu Software Center)
 

 **Download the following files**
 

 
[LIST]
[*]StepMania (in this case, version 5 	beta 1a)

[LIST]
[*]32-bit:


[LIST]
[*][http://sm-ssc.googlecode.com/files/StepMania-v5.0-beta1a-linux.tar.bz2](http://sm-ssc.googlecode.com/files/StepMania-v5.0-beta1a-linux.tar.bz2)
[/LIST]
 		
[*]64-bit:

[LIST]
[*][http://sm-ssc.googlecode.com/files/StepMania-v5.0-beta1a-linux64.tar.bz2](http://sm-ssc.googlecode.com/files/StepMania-v5.0-beta1a-linux64.tar.bz2)
[/LIST]
 	
[/LIST]
 	 	
[*]libpng15 (libpng15.so.15):

[LIST]
[*][http://sourceforge.net/projects/libpng/files/libpng15/1.5.15/libpng-1.5.15.tar.gz/download](http://sourceforge.net/projects/libpng/files/libpng15/1.5.15/libpng-1.5.15.tar.gz/download)
[/LIST]
 	 	
[*]libglew1.8

[LIST]
[*]32-bit:

[LIST]
[*][http://security.ubuntu.com/ubuntu/pool/main/g/glew/libglew1.8_1.8.0-1ubuntu2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glew/libglew1.8_1.8.0-1ubuntu2_i386.deb)
[/LIST]
 		
[*]64-bit:

[LIST]
[*][http://security.ubuntu.com/ubuntu/pool/main/g/glew/libglew1.8_1.8.0-1ubuntu2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glew/libglew1.8_1.8.0-1ubuntu2_amd64.deb)
[/LIST]
 	
[/LIST]
 	 	
[*]Stepmania icon

[LIST]
[*]google stepmania and find a 		desirable picture for an icon (.png preferred)

[LIST]
[*]name it stepmania.png
[/LIST]
 	
[/LIST]
 
[/LIST]
 

 

 Installing libpng15
 

 Go to Downloads and locate file “libpng-1.5.15.tar.gz” >> right click >> EXTRACT HERE
 

 Open TERMINAL and type the following:
 [TABLE="class: outer_border, width: 500"]
 	 	[TR]
 		[TD="width: 100%"] 			cd Downloads/libpng-1.5.15

 			
			
 			./configure –prefix=user/local/libpng
 			make check

 			sudo make install
 			make check
 		[/TD]
 	[/TR]
 [/TABLE]
 

 

 Now that you have the libpng15 installed, it's time to make a shortcut for the computer to use:
 assuming you are using the same terminal window:

 [TABLE="class: outer_border, width: 500"]
 	 	[TR]
 		[TD="width: 100%"] 			cd

 			sudo updatedb                            (this could take a few 			seconds)

 			locate libpng                              (locate the 			“.../libpng15.so.15” and copy the entire line)
 		[/TD]
 	[/TR]
 [/TABLE]
 

 Now we will create a NEW LINK (shortcut) of the file to “/usr/lib/”
 assuming you are using the same terminal window:
 [TABLE="class: outer_border, width: 500"]
 	 	[TR]
 		[TD="width: 100%"] 			sudo ln -s /usr/local/libpng/lib/libpng15.so.15 			/usr/lib/libpng15.so.15

 		[/TD]
 	[/TR]
 [/TABLE]
 

 CONGRATS! 1 of 3 Complete
 

 Installing libglew1.8
 

 locate the libglew1.8 >> double click >> install via Ubuntu Software Center
 

 CONGRATS! 2 of 3 Complete
 

 Installing STEPMANIA
 

 locate stepmania (i386 or amd_64).tar.bz2 and extract it to DESKTOP
 assuming you are using a NEW terminal window:
 [TABLE="class: outer_border, width: 500"]
 	 	[TR]
 		[TD="width: 100%"] 			cd Desktop/stepmania

 			./stepmania
 		[/TD]
 	[/TR]
 [/TABLE]
 

 CONGRATS! 3 of 3 Complete
 you have now installed stepmania completely, now we just need to clean things up. As you know, things can look a little messy and opening a file can be a hassle. So lets create a launcher and clean up the mess.
 

 Neat Setup
 Create a Launcher  
 
**1. Neat Setup**




 
[LIST]
[*]Go to Desktop and open the 	stepmania folder.

[LIST]
[*]_Select all, Cut._  		
[/LIST]
 	 	
[*]Go to home folder and Show Hidden 	Files **(View Tab > Show Hidden Files)**

[LIST]
[*]locate _.stepmania-5.0_ and 		open folder

[LIST]
[*]_Paste_ files here.  			
[/LIST]
 		 	
[/LIST]
 	 	
[*]Neat Setup Compete

[LIST]
[*]You may delete the stepmania 		folder on the Desktop.  		
[/LIST]
 	 
[/LIST]
 
**2. Create a Launcher**

Google "StepMania Icon" and select a suitable icon and save it as "stepmania.png" in home folder /.stepmania-5.0
 
[LIST]
[*]sudo gedit 	/usr/share/applications/StepMania.desktop

[LIST]
[*]password prompt  		
[/LIST]
 	 	
[*]Type/Copy the following:  	
[/LIST]
 

 [TABLE]
 	 	[TR]
 		[TD="width: 100%"] 			[TABLE="class: outer_border, width: 500"]
[TR]
[TD][Desktop 			Entry]
Version=5.0beta
Type=Application
Terminal=false
StartupNotify=true
Icon=/home/(YOUR_USERNAME)/.stepmania-5.0/stepmania.png
Name=StepMania
Comment=StepMania
Exec=/home/YOUR_USERNAME)/.stepmania-5.0/stepmania
Categories=Application; 			Games;
[/TD]
[/TR]
[/TABLE]
 		[/TD]
 	[/TR]
 [/TABLE]
 



 
[LIST]
[*]SAVE and Close

[LIST]
[*][COLOR=#ff0000]_**If 		for some reason it won't save, click Save as... and save it on:**_[/COLOR]

[LIST]
[*]File System: 			_/usr/share/applications_  			
[/LIST]
 		 	
[/LIST]
 	 
[/LIST]
 


CONGRATULATIONS! You have successfully, manually installed StepMania


BONUS: ADDING SONGS!!!


 
[LIST]
[*]on the home folder, Show Hidden 	Folders and open .stepmania

[LIST]
[*]CREATE a Songs folder  		
[/LIST]
 	 	
[*]On [www.stepmania.com]("http://www.stepmania.com/") 	download songs on the Download category

[LIST]
[*]extract your downloaded songs and 		put them in the Songs folder of the hidden .stepmania-5.0 folder 		located in the home folder when Show Hidden File is checked.  		
[/LIST]
 	 
[/LIST]
 


**ENJOY**


*TIP:*


[I]There are some DDR .smzip out there. Search the web for more info.
With a controller or Dance Pad, Go to Options to configure button/key mapping.[/I]

---

