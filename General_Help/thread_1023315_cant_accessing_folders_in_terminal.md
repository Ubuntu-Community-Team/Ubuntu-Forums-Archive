---
title: "cant accessing folders in terminal"
date: 2008-12-27
forum: General Help
---

### Post by navigator25 on 2008-12-27
Sorry if there is another topic on this subject, the only one i found was a read only version. [http://ubuntuforums.org/showthread.php?t=203752]("http://ubuntuforums.org/showthread.php?t=203752")
I am using Version 8.10 32 bit.

I am having troubles viewing folders in my terminal window. Im trying to view a folder i created. the location of it is /home/kyle/depot. When i do the command 
```
cd /home/kyle/depot 
```
I get an error message 
```
kyle@kyle-laptop:~$ cd /home/kyle/depot
bash: cd: /home/kyle/depot: No such file or directory
kyle@kyle-laptop:~$ 
```
I have tried multiple commands that were supposed to get me in this folder. The best i can do is get into the home folder for "/home" I can get into that from cd /home or cd ~/home. I tried to get into any other folder and i end up with the same results as the depot folder. 

What has really confused me is it knows the location of the folder im trying to access without using the full location command.
```
kyle@kyle-laptop:~$ cd ~/depot
bash: cd: /home/kyle/depot: No such file or directory
kyle@kyle-laptop:~$ 
```
I have read other places where i should be using the sudo command however there is nothing that works with that. 

```
kyle@kyle-laptop:~$ sudo cd /home/kyle/depot
[sudo] password for kyle: 
sudo: cd: command not found
kyle@kyle-laptop:~$ sudo cd ~/depot
sudo: cd: command not found
kyle@kyle-laptop:~$ sudo -s cd /depot
/bin/bash: cd: No such file or directory
kyle@kyle-laptop:~$ 
```

Im new to Ubuntu so i dont know all commands etc. If you can please be detailed in answers. Thanks for the help I hope i provided enough information.

---

### Post by taurus on 2008-12-27
What's the output of this command from a terminal?

```
ls -la ~
```
Remember, Unix/Linux is case sensitive so lower case letter is not the same as upper case letter.

---

### Post by navigator25 on 2008-12-27
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la ~
```
Remember, Unix/Linux is case sensitive so lower case letter is not the same as upper case letter.
Some how my folder was uppercase, i didnt remember doing it in uppercase, but it worked when i did that.

Thanks and thats a great thing to know too.

---

### Post by taurus on 2008-12-27
You can change it to lower case if you wish.

```
mv DEPOT depot
```

---

### Post by navigator25 on 2008-12-27
> **taurus said:**
> You can change it to lower case if you wish.

```
mv DEPOT depot
```

Ok good to know since i would prefer to have it lowercase, i normally try to make everything same, kinda weird about that since i try to have most of my coding in lowercase unless it needs to be Upper.

Since only the "D" is I would assume i do 
```
mv Depot depot
```?

Thanks again

---

### Post by SuperSonic4 on 2008-12-27
Yes, that's correct :]

---

### Post by snova on 2008-12-27
Ubuntu is case-sensitive. 'Depot' is not the same as 'depot', nor is 'DEPOT'.

'cd /home/kyle/Depot' is the same as 'cd ~/Depot', as ~ is expanded to your home directory.

When you run 'sudo cd', sudo looks for a program called 'cd': and there isn't one, so that's why it doesn't work. cd is built into the shell.

---

