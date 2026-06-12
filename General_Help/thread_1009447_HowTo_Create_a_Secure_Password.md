---
title: "HowTo: Create a Secure Password"
date: 2008-12-12
forum: General Help
---

### Post by Sorivenul on 2008-12-12
A while ago I read an interesting [blog entry]("http://php.8ez.com/drsmall/blog/?p=273") from [Dr Small]("http://ubuntu-virginia.ubuntuforums.org/member.php?tab=friends&u=197439&pp=10&page=3") on a simple method to create secure passwords.

I have taken the liberty of reposting the method below:

1.) Choose two words that are meaningful to you, make note of the exact spelling and capitalization.

2.) Open a terminal.

3.) Type following:
```
echo "word1" > out1
echo "word2" > out2
```
"out1" will contain the word "word1", and "out2" will contain the word "word2".

4.) Create an MD5 hash of each word and store it in a file called "hash":
```
md5sum out1 >> hash
md5sum out2 >> hash
```
The "hash" file should now look like this:
> 0ab0f9489f1fb16837aa87a98dc4b877  out1
ae723c18cd13cbe875842f2061b8f4d9  out2

5.) Remove "out1" and "out2" from end of each line in the "hash" file using your favorite editor.

6.) Create an MD5 hash of the "hash" file:
```
md5sum hash
```
This should generate a 32 character hash, like:
> e86d46105c672bbd679178aad9b41b87
You can choose as many characters as you want for your password.

7.) Change your password.  On Ubuntu this can be done a few different ways.  
Graphically: System > About Me > Change Password...
Terminal:
```
passwd $USERNAME
```
Enter your current password, then enter the new password twice to confirm.

This may seem a little complex, especially if you are a new user simply looking to secure your system.

For this purpose, I have written a simple, graphical Python program "PySumpas" that allows you to do the same thing.  It is available on [SourceForge]("http://sourceforge.net/projects/pysumpas"), and can also be tracked through [Launchpad]("http://launchpad.net/pysumpas"). For users here the latest release requires [python-crypto]("apt://python-crypto") and [python-tk]("apt://python-tk"), both available in the Ubuntu repositories, as well as Damien Miller's py-bcrypt, which is available in the repositories for version 8.10+ as [python-bcrypt]("apt://python-bcrypt"), or [here]("http://www.mindrot.org/projects/py-bcrypt/") if you are running a previous version of Ubuntu.  You do not need to use PySumpas, but it eliminates the creation of the files from the original method and provides a more comfortable interface for those not wishing to use the command line.

If you choose to install PySumpas, there is little terminal work that needs to be done. The PySumpas README has information on how to install, but for the sake of thoroughness, I will include a simple method here.

1.) Download PySumpas. If you use Firefox, it will most likely be saved to your Desktop.
2.) Extract PySumpas, which is in a tar.gz archive or tarball. You can do this graphically using the archiving tools on your system, or from a terminal:
```
tar -xvf /path/to/pysumpas-0.4.0.tar.gz
```
Replace the "0.4.0" with the version you downloaded. This will extract PySumpas to a directory named "pysumpas-0.4.0" in your Home folder.
3.) Make sure the file "pysumpas.py" is executable:
```
chmod +x /path/to/pysumpas.py
```
4.) Copy the file to your /usr/local/bin directory:
```
sudo cp pysumpas.py /usr/local/bin
```

You should then be able to launch PySumpas from the terminal using:
```
pysumpas.py
```

If you don't want to type "pysumpas.py" to launch the program, do:
```
sudo ln -s /usr/local/bin/pysumpas.py /usr/local/bin/pysumpas
```
This will create a symlink; so to run the program you will only have to type:
```
pysumpas
```

If you have any questions regarding the orginal method or PySumpas, feel free to contact me.

---

### Post by greavis on 2010-11-01
Or just use [www.passwordcake.com](www.passwordcake.com) :)

---

### Post by Megaptera on 2010-11-01
I like PasswordCard:

[http://www.passwordcard.org/en](http://www.passwordcard.org/en)

---

