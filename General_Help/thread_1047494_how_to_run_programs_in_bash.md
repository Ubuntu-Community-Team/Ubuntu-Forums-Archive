---
title: "how to run programs in bash"
date: 2009-01-22
forum: General Help
---

### Post by ario on 2009-01-22
Hi
I want to write a bash scripts that runs three programs togather. I know that it is as easy as write their names in my script and then run script to execute them. but the problem is that the scripts run first program. waits for it to finished. then second and the the third.
for excample if i want to run three instances of gcalctool program the scripts runs one at a time and wait until it finished to run next commands:

```
#!/bin/bash
gcalctool
gcalctool
gcalctool

```
I want to put this script in ubuntu startup to run all of my favorit applications in special times. but my problem is that the script runs only first application as I said.
Anyone have idea how to run all of theme without waiting to finish each of theme?

---

### Post by azr on 2009-01-22
Only a slight modification is necessary:

```

#!/bin/bash
gcalctool &
gcalctool &
gcalctool &

```

---

### Post by sedawk on 2009-01-22
Lesson 2 ;-)

```

#!/bin/bash
nohup gcalctool &
nohup gcalctool &
nohup gcalctool &
wait

```

nohup will make sure that closing the terminal by accident does not
kill the running gcalctool.
wait will wait for all childs to finish, so you can use wait to
make sure the script doesn't end before the started tools are finished.

---

### Post by ario on 2009-01-23
God Bless you men!
You have solved my problem. Thank you!

---

### Post by fragos on 2009-01-23
Also make sure your home grown scripts are are maked as executable and in folders that will be checked for executables. I put all mine in /usr/local/bin. You can see where executables are kept by running "echo $PATH".

---

### Post by ario on 2010-10-02
> **fragos said:**
> Also mack sure your home grown scripts are are maked as executable and in folders that will be checked for executables. I put all mine in /usr/local/bin. You can see where executables are kept by running "echo $PATH".

Thanks in advance:)

---

