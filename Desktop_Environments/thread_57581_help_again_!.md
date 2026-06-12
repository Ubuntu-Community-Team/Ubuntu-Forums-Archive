---
title: "help again !"
date: 2005-08-17
forum: Desktop Environments
---

### Post by ceborame on 2005-08-17
I'm having a lot of trouble installing software using the terminal

I want to install Java runtime; these are the instructions.

I'm stuck from step 1 lol

	    Installation Instructions


To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-1_5_0-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l



Make sure the installation file has executable permission

   6. Start the installation process.Type:
      ./jre-1_5_0-linux-i586.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

   7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.5.0 directory. When the installation has completed, you will see the word Done.



The installation completes

   8. The JRE is installed in jre1.5.(version number) sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.5.0 directory. Verify that the jre1.5.0 sub-directory is listed under the current directory. Type:
      ls



Verify the installation filename

The installation is now complete. Skip to the Enable and Configure section.

Kind regards

Mick

---

### Post by JLTB on 2005-08-17
An easier way (the ubuntu way :D),

If you don't have it already, add the ubuntu backports to your sources list (edit the file /etc/apt/sources.list, ie: "sudo vi /etc/apt/sources.list")

Add the following 2 lines to the file

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main restricted universe multiverse

```

Then just install java!

```

sudo apt-get install j2sdk-1.5

```

That should do it :)

PS: Of course If you want a different version of java you will have to choose a different route, but this will get you the full SDK and the JRE.

---

### Post by ceborame on 2005-08-17
thanks.

I just want jre so I can use azureus

Kind regards

Mick

---

