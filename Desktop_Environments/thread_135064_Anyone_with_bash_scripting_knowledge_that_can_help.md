---
title: "Anyone with bash scripting knowledge that can help me with this?"
date: 2006-02-23
forum: Desktop Environments
---

### Post by ardchoille on 2006-02-23
I have a [nice script]("http://www.ubuntuforums.org/showthread.php?t=134976") that automates the whole process of copying a DVD movie, but I'd like to enhance that script in the following way.

I would like to learn how to put a pause/question in the script that pauses everything, asks the user a yes/no question and then continues based on the users' response. Basically the script runs dvdbackup (it's in the repos) to copy a DVD movie, then runs mkisofs to create an image of the copy, then runs growisofs to burn the image to a blank DVD. something like this:

1) run dvdbackup and copy the DVD

2) ask the user if he/she would like to continue on with the next step (mkisofs) and continue if they choose yes or stop the script (exit 1?) if they choose no

3) ask the user if he/she would like to continue on with the next step (growisofs) and continue if they choose yes or stop the script (exit 1?) if they choose no. This one is good for people who only have one dvd burner drive and need to swap out the DVD movie that was copied for a blank DVD before the burning process. I have a dvd reader and a dvd burner so the script is ok as is, but I want to enhance it and make it more interactive for other people.

4) add the possibility of ejecting one or both disks after the burn is done.

5) add the possibility of deleting the DVD project directory or the dvd image or both.

How do I create command line questions in a bash script, wait for user input and then continue on depending on the answer the user chose?

Something like "Would you like to continue (yes/no/abort)?"

---

### Post by kabus on 2006-02-23
> How do I create command line questions in a bash script, wait for user input and then continue on depending on the answer the user chose?

Something like "Would you like to continue (yes/no/abort)?"

```
echo "Would you like to continue (yes/no/abort)?"
read
case $REPLY in
  yes|y) do something;;
   no|n) do something else;;
abort|a) exit 0;;
    *) echo "Usage:..." ;;
esac
```

---

### Post by suRoot on 2006-02-23
Here's a basic example...

```
while true; do
  echo -n "Install baz? (y/n) "
  read yn
  case $yn in
    y* | Y* ) command ; break ;;
    [nN]* )   echo "Not Installing baz" ; break ;;
    q* ) exit ;;
    * ) echo "Enter yes or no" ;;
  esac
done 
```

---

### Post by ardchoille on 2006-02-23
Great stuff :)
Thank you.. I am a happy camper :)

---

