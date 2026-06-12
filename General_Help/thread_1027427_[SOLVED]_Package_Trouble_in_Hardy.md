---
title: "[SOLVED] Package Trouble in Hardy"
date: 2009-01-01
forum: General Help
---

### Post by u'b'u'n't'u on 2009-01-01
I was trying to upgrade to 8.10, but when I went to the Update Manager a blank window appeared with a triangular warning sign. When I go into synaptic i get this message:

E: Type '<!DOCTYPE' is not known on line 3 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

when i go to add/remove programs i get this:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

i am a noob so use kiddie terms:confused::confused:

---

### Post by taurus on 2009-01-01
There is something with your /etc/apt/sources.list.d/medibuntu.list.

```
cat /etc/apt/sources.list.d/medibuntu.list
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by drs305 on 2009-01-01
You most likely just have a bad entry in sources.list.

Back it up and open for editing:
```

sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.backup
gksudo gedit +3 /etc/apt/sources.list.d/medibuntu.list

```

This will open medibuntu.list on line 3, the line with the problem. Place a comment symbol ( # ) at the start of the line and save the file. Then run:
```

sudo apt-get update

```

If that was the only error, you shouldn't get any errors. If you have multiple problems with your sources.list, it would probably be best to post it here with any resulting error messages.

---

### Post by u'b'u'n't'u on 2009-01-01
i got this:


luke@luke-laptop:~$ sudo apt-get update
[sudo] password for luke: 
E: Type '<html' is not known on line 4 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by drs305 on 2009-01-01
You probably have several errors. You can post the results of the following and we can look at it, or you can accomplish the later commands to fix this yourself:
```

cat /etc/apt/sources.list.d/medibuntu.list

```

It is possible you have the wrong version of the medibuntu sources.list (it is specific to the ubuntu version you are running). 

Most likely you can resolve the problem easily by running one of the following sets of commands to reset your medibuntu.list:

For Hardy:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

For Intrepid:
```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by u'b'u'n't'u on 2009-01-03
thank you very much. synaptic worked perfectly. I love Ubuntu's simplicity.

---

