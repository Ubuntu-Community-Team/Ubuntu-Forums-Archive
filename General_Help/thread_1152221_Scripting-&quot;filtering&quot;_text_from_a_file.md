---
title: "Scripting-&quot;filtering&quot; text from a file"
date: 2009-05-07
forum: General Help
---

### Post by RjBanker18 on 2009-05-07
Hello all,
I am working on my first shell script.  I am stuck at this point and I can't seem to find any documentation that tells how to deal with it!  I have a script that takes text from a log file and I want it to remove parts so that only one word remains in a variable $log.  Then it will use an If, Then, Else to display a message using zenity.
Here is what I have so far:
```
log=$(cat UpgradeSHLog.txt|grep Err|sed 's/ h.*//g'|sed 's/ E.*//g')

if $log=Err

then

zenity --error --text="Upgrade Failed.  Please make sure you are connected to the internet."

else

zenity --info --text="Upgrade Successful."

fi
```

Here is an echo of the variable afterward:
```
echo $log
Err Err Err Err Err Err Err Err Err Err Err Err Err Err Err
```
When I put in the commands that make up the $log variable by itself it shows this:
```
cat UpgradeSHLog.txt|grep Err|sed 's/ h.*//g'|sed 's/ E.*//g'
Err
Err
Err
Err
Err
Err
Err
Err
Err
Err
Err
Err
Err
Err
Err
```
Maybe the reason why it leaves multiple "Err"s is because the output from the logfile has returns with multiple lines?  Maybe you can tell me!:)

How would I go about removing all the "Err"s but one?  Also, maybe there is there a better way of doing this?

Thanks!

---

### Post by Kegusa on 2009-05-07
A little hint, you are piping the output of "grep Err" to your sed statements. Tried awk? and what does your log files look like in the original state?

---

### Post by RjBanker18 on 2009-05-07
> **Kegusa said:**
> A little hint, you are piping the output of "grep Err" to your sed statements. Tried awk? and what does your log files look like in the original state?

If I don't pipe "grep Err" then I get this:
```
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
It is Thu May  7 13:56:12 CDT 2009
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
------------------------------------------------------------------
UPDATING REPOSITORIES...
------------------------------------------------------------------
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'us.archive.ubuntu.com'
Err
  Could not resolve 'security.ubuntu.com'
Err
  Could not resolve 'security.ubuntu.com'
Err
  Could not resolve 'security.ubuntu.com'
Err
  Could not resolve 'security.ubuntu.com'
Err
  Could not resolve 'security.ubuntu.com'
Reading package lists...
```

I had a lot of trouble figuring out sed, I checked the "awk" (now mawk?) man pages and it's not exactly friendly to read.  Could I have an example of how to use it?

The original log:
```
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
It is Thu May  7 13:56:12 CDT 2009
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
------------------------------------------------------------------
UPDATING REPOSITORIES...
------------------------------------------------------------------
Err http://us.archive.ubuntu.com jaunty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com jaunty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com' 
Reading package lists...
```

This script I am making is for fun and to see what I can do!
Thanks

---

