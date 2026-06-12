---
title: "AMSN installing"
date: 2009-02-24
forum: General Help
---

### Post by Mulliganiscool on 2009-02-24
Hi.. so recently I installed amsn from the add and remove option.. and i wanted to get plugins.. so i removed amsn and downloaded it from the website. i moved the plugins i wanted into the plugin folder for amsn.. but whenever i was done i tried to launch it and an error message popped up saying "loading tkcximage failed this module is needed to run amsn please compile amsn first instructions on how to compile are located in the file install" So i was like poop :'[ more work for me this sucks so i went to the amsn folder and found something that said "INSTALL" So then i was like yay maybe not so hard so I clicked
and this is what came up 
"In order to install amsn, or even to be able to launch it, you will need to compile it first.
To do so, you must first configure the package by executing the command
> ./configure
You must have the tcl-dev and tk-dev packages installed on your system, please refer to your system package management software or website in order to find these packages and to install them prior to running the ./configure script.
Once the configure script finished without any error, you can proceed with the compilation, it is as simple as typing :
> make
You can now launch amsn by typing 
> ./amsn
Or you can install it with the command
> make install
Then you can use the 
> amsn
command to launch future sessions of amsn.
You can also create a .deb and .rpm package by launching respectively the command
> make deb
and
> make rpm

For any other help, please refer to the FAQ at [http://amsn-project.net/faq.php](http://amsn-project.net/faq.php) or the wiki at [http://amsn-project.net/wiki](http://amsn-project.net/wiki) or the website at [http://amsn-project.net](http://amsn-project.net) or visit the forums of amsn at [http://amsn-project.net/forums](http://amsn-project.net/forums), but make sure you search for an answer to your question before asking it, it might have already been answered.

have fun." 





A whole bunch of words so i was like great :'[ 
 And I totally didn't know if i had the tcl-dev or tk dev packages so i was like hmn.. i grabbed my terminal and typed in the comands 
sudo apt-get install tcl-dev
(which it installed it im pretty sure)
sudo apt-get install tk dev 
(and it looked like it was installing )  
Then I typed in the commands 
> ./configure 
> make 
> ./amsn 
> make install 
> amsn
(this appeared to be doing nothing I don't know alot about this junnk so yea lol) 
and then
> make deb
>make rpm 



I don't know
also after a few tries instead of putting > make deb i put sudo apt-get install deb( which appeared to be doing soemthing) and sudo apt-get install rpm( which was doing something so lol)

---

### Post by gettinoriginal on 2009-02-24
I am just curious why you are trying to compile it when the one from Add/Remove could have been used to install the plugins ??  :confused:

---

### Post by Mulliganiscool on 2009-03-02
> **gettinoriginal said:**
> I am just curious why you are trying to compile it when the one from Add/Remove could have been used to install the plugins ??  :confused:

The folder for it i couldn't find it but i figured out how to do everything so yay me

---

