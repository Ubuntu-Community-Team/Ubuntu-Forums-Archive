---
title: "help with upgrading Java"
date: 2009-02-28
forum: General Help
---

### Post by trinidadflores on 2009-02-28
I need help updating my java.  I have downloaded the update to my desktop and i have followed the steps as listed on java, but it wont create the director for java.  ( To install the Linux RPM (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java

      Note about root access: To install Java in a system-wide location such as/usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install Java in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u<version>-linux-i586-rpm.bin
   5. Start the installation process. Type:
      ./jre-6u<version>-linux-i586-rpm.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

   6. The installation file creates jre-6u<version>-linux-i586.rpm file in the current directory.



RPM unpacking completes

   7. Run the RPM command at the terminal to install the packages. Type:
      rpm -iv jre-6u<version>-linux-i586.rpm
   8. Java is installed in jre1.6.0_<version> sub-directory under the current directory. In this case, Java is installed in the /usr/java/jre1.6.0_<version> directory. Verify that the jre1.6.0_<version> sub-directory is listed under the current directory. Type:
      ls



Verify the installation filename

The installation is now complete. Go to the Enable and Configure section.)

Currently what is installed is version is 1.6.0_0.

---

### Post by taurus on 2009-02-28
If you want to install java by hand, why not just get the .bin file instead of .rpm.bin?

---

### Post by trinidadflores on 2009-02-28
> **taurus said:**
> If you want to install java by hand, why not just get the .bin file instead of .rpm.bin?
where would i find that at?

What would the easist way be?

---

### Post by taurus on 2009-02-28
The same place that you downloaded the .rpm.bin.  RPM is more for RedHat/Fedora distro.  With .bin, you just unpack it in whichever directory you want to install and link to it.  No need to run that extra **rpm -i** step.

---

