---
title: "Photo Renaming Script Help"
date: 2006-09-30
forum: Desktop Environments
---

### Post by andy_cowman on 2006-09-30
Hey

I am writing a script to import JPGs and Raws from  memory card. I have it copying everything but I am struggling to get it to rename properly. I want to rename all the images with the date and the an individual number for the image. That way I never have duplicate names.

I have been reading posts but nothing seems quite right. I could rename them all but I don't know how to add the sequential numbering! Any ideas?

Thanks

Andy

---

### Post by elettronicha on 2006-09-30
If you don't want to loose your mind with bash-scripting, open synaptic and search "by name" (not by "description and name") the target "rename": you will find something.

---

### Post by aysiu on 2006-09-30
If you don't mind not using a script and using the GUI instead, KRename is a pretty powerful mass-renaming program.

---

### Post by curtisf14 on 2006-09-30
When you say you want the date of the image, do you mean the date that the file was last modified?  If so, this is how you would do it...

Let's say "imgdir" is the directory that all your images are in (replace it with whatever directory that contains your files).  Type this into the terminal:

```

cd imgdir
declare -i number=1
for x in $(ls *.jpg); do
time=$(ls -lo $x | awk '{print $5}')
mv $x ${x%.jpg}${time}_${number}.jpg
number+=1
done
unset number

```

That should do it.  If that's not what you want, you can look at the documentation for bash scripting at [http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by andy_cowman on 2006-09-30
The date I wish to put in is the date the image is downloaded to the computer, so essentially the date that the script is run in the directory.

Thanks very much for all the suggestions, especially the bash instructions! I shall look into it.

I wish to use a script as it does it automatically and its mostly going to be my father using it for his digital photography!

---

### Post by aysiu on 2006-09-30
I'm not 100% sure this has the exact feature you're looking for, but have you looked into F-Spot? It's in the repositories.
[http://f-spot.org/User_Guide/Organize#Import](http://f-spot.org/User_Guide/Organize#Import)

---

### Post by andy_cowman on 2006-09-30
I've tried F SPot and it just closes almost immeditely which is very frustrating. The importing straight from the camera can be done with digikam but doing that does add an extra step to the process. 

I was trying this

rename -v 's/\d{3}(\d{4})\.jpg$/TEST_$1\.jpg/' *.jpg

but it doesnt seem to do anything!

---

### Post by curtisf14 on 2006-10-01
If you put the above script in a bash script file, it should do the trick (I tested it on my machine and it works).  Have you tried it yet?  If you do, let me know how it turns out.  :-)

You can modify it so that it only changes files that you put as parameters to the script.  That way you won't accidentally run the script twice on the same files and get the file names looking weird...  If you would prefer that method of doing it, again, just let me know.

---

