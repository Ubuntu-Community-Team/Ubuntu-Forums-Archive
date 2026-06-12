---
title: "if Command Help!!!"
date: 2009-01-11
forum: General Help
---

### Post by andersensam on 2009-01-11
Hi all, I am currently working on universal Linux packaging. For my packages I am currently using the SZX format (just made it up for now), I currently have a installer file (need to make executable before using + un-tar)(is a bash script) I have the installer totally working but I want to make a "Are you sure you want to install this package: nameofpackage? I have Zenity asking for a user input but don't know how to make the installer respond to the input... Please help....

---

### Post by nemilar on 2009-01-11
I have no idea what Zenity is, but in bash it would be:

```

read -p "Do you want to continue? [y/N]: " answer
if [ $answer == "y" ] 
then
	echo "Answered yes, doing stuff..."
else
	echo "Did not answer yes, doing something else..."
fi

```

Which outputs the following:

```

jdeprizi@enterprise:~/temp$ bash temp.bash 
Do you want to continue? [y/N]: y
Answered yes, doing stuff...
jdeprizi@enterprise:~/temp$ bash temp.bash 
Do you want to continue? [y/N]: n
Did not answer yes, doing something else...

```

---

