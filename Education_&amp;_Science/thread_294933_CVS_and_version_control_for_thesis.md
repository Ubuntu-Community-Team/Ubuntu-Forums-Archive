---
title: "CVS and version control for thesis"
date: 2006-11-07
forum: Education &amp; Science
---

### Post by neoflight on 2006-11-07
Folks,

I was wondering, has anyone used CVS to aid thesis writing?
A how to would be welcome. I think its good to have a version control system (locally) for thesis writing. Its difficult to keep track of various changes in a 300 page document written over many years.

I keep adding 'latest' to the end of the filename to indicate the version and its alway the 'latest' everytime i change/add something. This happens because of rush or urgency. After sometime its painful.

Any ideas? Thanks

---

### Post by Felipe_U on 2006-11-07
I wish I had that idea when I was writing my final proyect to get out of University. Dealing with version control is a pain in the ***. I do believe is posible to do it, I have Subversion installed since I read that it was like a more advance CVS. I'll give it a try on the weekend if I have the time. I think I'll try with an open office document and a Lyx document. 

Also, Do you know you can write documents online with google docs? it has version control, and you can export to several formats.

Regards,
Felipe

---

### Post by dwight on 2006-11-07
I used Subversion when writing my BSc thesis. (Subversion or SVN is sort of an updated/enhanced version of CVS). I did not, however, host the repository on my machine, but on a different server - so as to also be able to access my work from other workstations. You can actually find sites that offer a free svn/cvs repository. Of course it might not be desireable to have your work on a third-party server and in this case keeping the repo on your own machine is a entirely viable option. There's a nice intro to setting up single-user svn on a machine [here](http://www.onlamp.com/pub/a/onlamp/2002/10/31/subversion.html). You can skip the compilation part, as svn is easily installed via synaptic.

---

### Post by Steveire on 2006-11-07
Hi. I'm very interested but confused.

I am going to start a college project soon using python. I'd like version control on the python project and on my latex files that I'll edit in kile. I tried following the link you gave, but here's my output from it:
```

stephen@ubuntu:~/fyp/svn/db$ svn mkdir file:///home/stephen/fyp/svn/report -m 'Create report'

Committed revision 1.
stephen@ubuntu:~/fyp/svn/db$ svn import /home/stephen/fyp/report/ file:///home/stephen/fyp/svn report/trunk -m 'Initial import of report'
svn: Too many arguments to import command
stephen@ubuntu:~/fyp/svn/db$     

```
Can you tell me how to fix this please? Also, will it be straightforward for me to link kile into the svn repo? I also looked around kdevelop to see if I could link my python project files into the svn. I also downloaded kdesvn, but couldn't find anywhere in it that said create new or anything. If you can give me help it would be much appreciated.

---

### Post by LaserJock on 2006-11-08
I think bzr would make an excellent tool for this. It doesn't require a repository or a server. You just run bzr init in the directory and there you go. You can move the directory wherever you want and it doesn't matter. I use it a fair amount for local revision control. It's also developed by Canonical and use extensively by Ubuntu.

-LaserJock

---

### Post by roderikk on 2006-11-08
> **LaserJock said:**
> I think bzr would make an excellent tool for this. It doesn't require a repository or a server. You just run bzr init in the directory and there you go. You can move the directory wherever you want and it doesn't matter. I use it a fair amount for local revision control. It's also developed by Canonical and use extensively by Ubuntu.

-LaserJock
Hm, I installed bzr, after also reading about it on the blog of Mark, but after reading the manpages confusion reigns... :-) Can you give some pointers and or tutorials?

---

### Post by neoflight on 2006-11-08
Thanks for all the replies. I guess there are several people interested including my friends here in school. Version control is really a pain. and I like the idea of setting up the server at one of the school network so that i can access from anywhere and also will act as a back up. the chances of screwing up my system is far greater than server. 

Subversion seems to be good. will try and let you know. thanks...

more ideas and how-to's are welcome...:)

---

### Post by Felipe_U on 2006-11-08
> **Steveire said:**
> Hi. I'm very interested but confused.

I am going to start a college project soon using python. I'd like version control on the python project and on my latex files that I'll edit in kile. I tried following the link you gave, but here's my output from it:
```

stephen@ubuntu:~/fyp/svn/db$ svn mkdir file:///home/stephen/fyp/svn/report -m 'Create report'

Committed revision 1.
stephen@ubuntu:~/fyp/svn/db$ svn import /home/stephen/fyp/report/ file:///home/stephen/fyp/svn report/trunk -m 'Initial import of report'
svn: Too many arguments to import command
stephen@ubuntu:~/fyp/svn/db$     

```Can you tell me how to fix this please? Also, will it be straightforward for me to link kile into the svn repo? I also looked around kdevelop to see if I could link my python project files into the svn. I also downloaded kdesvn, but couldn't find anywhere in it that said create new or anything. If you can give me help it would be much appreciated.
Hi, I'm not really sure what you did there. But here is how I do it:[LIST=1]
[*]Create a directory for the repository: ```
mkdir /home/felipe/svn-repos
```
[*]Use svnadmin to make the directory I just created a repository: ```
svnadmin create /home/felipe/svn-repos
```
[*]Move to the directory where you have the initial files for your proyect and import them: ```
svn import -m "Importing initial files" . file:///home/felipe/svn-repos/<proyect name>/trunk
```
[*]To check out a working copy, move to the direcotry where you want your working copy created and type: ```
svn co file:///home/felipe/svn-repos/<proyect name/trunk <proyect name>
```[/LIST][LIST]
[*]A working copy will be created with the name of your proyect and the files you initially imported on step 3
[*]You can download a book about svn here [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)[/LIST]Regards,
Felipe

---

### Post by Felipe_U on 2006-11-08
> **roderikk said:**
> Hm, I installed bzr, after also reading about it on the blog of Mark, but after reading the manpages confusion reigns... :-) Can you give some pointers and or tutorials?

You can find tutorials here: [http://bazaar-vcs.org/Documentation](http://bazaar-vcs.org/Documentation)

---

### Post by ssam on 2006-11-08
what are you writing the thesis with? unless it is plain text, or latex or something similar then versioning systems wont help much.

a diff between two binary files does not mean very much, but a diff between two text files shows you exactly what changed.

you can use SVN locally. there is a repository folder, that holds a database of all the revisions. and a local folder where you make you changes. have a look at the SVN book for info [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

if you want a much simpler solution (what i use for labreports). just name each days file with a date and revision number eg

lab-report-20061106-1
lab-report-20061107-1
lab-report-20061107-2

(use YYYYMMDD for the date so that they are in the correct order when you sort by filename).

---

### Post by dwight on 2006-11-08
[The Top Ten Subversion Tips for CVS Users](http://www.onlamp.com/pub/a/onlamp/2004/08/19/subversiontips.html?page=1). Despite the title these tips are useful even if you have no experience with cvs.

---

### Post by neoflight on 2007-05-14
just to bring it up to current...if you have any new information to add....i screwed up with my local cvs repos....

---

### Post by ssam on 2007-05-15
i have just finished a ~5000 work lab report in Latex. I used SVN this time.

I have made a local svn repo for all my uni projects at /home/sam/docs/subversion/physics . this was created with

```
svnadmin create --fs-type fsfs /home/sam/docs/subversion/physics
```

to look at what is in the repo once you have made it use

```
svnlook tree /home/sam/docs/subversion/physics
```

to import an existing directory of work, move into its folder and run

```
svn import . file:///home/sam/docs/subversion/physics/NEW_PROJ_NAME -m "import of NEW_PROJ_NAME"
```

now use the svnlook command again to check that it has imported.

the slightly awkward bit is that the folder you just used to make the import is not a work copy. this means that svn will not manage it. in theory you can delete it and then check it out working copy from the repository. personally i would move it to a safe place.

now you can checkout a working copy of you project. do this with

```
svn co file:///home/sam/docs/subversion/physics/NEW_PROJ_NAME dirname
```
if you move into this directory you and run
```
ls -a
```
you will see that there is a .svn folder. this lets svn keep track of what changes you have made to your working copy.

now you can start work in your working copy. to list the changes you have made run
```
svn diff
```
to see which files you have modified or added run
```
svn status
```
to commit the current changes run
```
svn commit -m "a comment about the changes"
```

if you create a new file it will show with a '?' in the status list. this means that svn  does not know what to do with it. some times you want svn to ignore files, for example you dont want it to store the compiled version of a program, only the source code. to tell svn to start keeping track of a file run
```
svn add filename
```

---

### Post by roderikk on 2007-05-16
I have recently made the switch from svn to bzr. The commands are all the same but it is much easier to set up a repo and also to push to somewhere external (ie a webserver).

Check: [http://bazaar-vcs.org/](http://bazaar-vcs.org/)

---

### Post by skywatcher on 2007-05-16
That's what I do in MATLAB --  save the day's work with something like 'save session_2007_02_15'

---

### Post by jjvenkit@uwaterloo.ca on 2007-06-21
Anyone care to reply with info on how to do exactly this but from a local machine (like a laptop) via ssh to another machine (server somewhere else).  Essentially, what are the short instructions on how to do this with a remote repo?

Thanks.

---

### Post by LaserJock on 2007-06-22
> **jjvenkit@uwaterloo.ca said:**
> Anyone care to reply with info on how to do exactly this but from a local machine (like a laptop) via ssh to another machine (server somewhere else).  Essentially, what are the short instructions on how to do this with a remote repo?

Thanks.

What specifically are you wanting to do? With bzr you could easily have the revision control locally and then rsync or scp the .bzr/ directory to the remove server to backup/store.

-LaserJock

---

### Post by UbuWu on 2007-06-26
> **neoflight said:**
> Folks,

I was wondering, has anyone used CVS to aid thesis writing?
A how to would be welcome. I think its good to have a version control system (locally) for thesis writing. Its difficult to keep track of various changes in a 300 page document written over many years.

I keep adding 'latest' to the end of the filename to indicate the version and its alway the 'latest' everytime i change/add something. This happens because of rush or urgency. After sometime its painful.

Any ideas? Thanks

[Mnemosyne]("https://launchpad.net/mnemosyne") could be exactly what you want. It is a google summer of code project that makes your home folder version controlled, so all your documents would be version controlled. Only problem is that it isn't available yet, but it should be at the end of august.

---

### Post by hutxubix on 2008-02-05
Hey!

What about GUIs for svn? What do you think about them?

I have seen subcommander (I have had problems in ubuntu) and rapidsvn (I would say not very developed yet).

Any others?

---

### Post by amar on 2008-02-25
I have just setup bazaar to track my work. I noticed that all my work is either a project (HTML, Java script etc) or a latex report and a version control would be a simple method of backup and allow me to use more than one workstation.

I have to commend the documentation on the bazaar website, made it very easy to set up and was nice and friendly. It appears to cater well for simple systems (on the same computer) and is very flexible.

---

### Post by zadig on 2008-02-25
_Setting up a CVS:_

set up a repository 
root@localhost:~> mkdir /usr/local/cvsrep
root@localhost:~> chown userName /usr/local/cvsrep
root@localhost:~> chmod g+w /usr/local/cvsrep
root@localhost:~> exit

liz@localhost:~> export CVSROOT=/usr/local/cvsrep
liz@localhost:~> cvs init
This will create some files, under /usr/local/cvsrep 
dont mess up those files. 


_First project: _
Go under your thesis directory 
cd ~/UbuntuThesis
cvs import -m "Some String ie Thesis" cvsDirName vendor-tag start
This will create some files, under /usr/local/cvsrep 
dont mess up those files. 

Some usefull commands
    * cvs add file_name     --> indicates that file_name is to be added to the repository (once a 'cvs commit...' is done)
    * cvs remove file_name     --> indicates that file_name is to be removed from the repository (once a 'cvs commit...' is done)
    * cvs commit -m "The message..."     --> will commit any files that you've changed in your working directory into the repository
    * cvs commit -m "The message..." file_name     --> will commit the file file_name
    * cvs log [file_name]     --> prints log info [of file_name] to stdout (pipe this to a file if you want to view the log) 


and see this for using ssh with cvs,
[http://www.hurring.com/scott/howto/cvs_ssh/](http://www.hurring.com/scott/howto/cvs_ssh/)

-catay

---

### Post by ulver on 2008-03-11
Is there a svn package that I can install on a ubuntu server that windows guest connect to allowing them to use svn features without ssh?

---

