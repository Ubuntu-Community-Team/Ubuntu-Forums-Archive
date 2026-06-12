---
title: "Safe Erase/Delete"
date: 2009-03-01
forum: General Help
---

### Post by Paskinel on 2009-03-01
-How can I safely Erase/Delete Files and Folders?

-Is there any **Ubuntu** program (like Eraser in Wind-ow$...)
that uses Sefe Erase/Delete Overwriting Methods
(i.e. DoD-3, DoD-7, Guttman 35)?

---

### Post by msrinath80 on 2009-03-01
There is a command called shred in GNU/Linux that does this.

```
shred filename
```

For more information try 'man shred'

---

### Post by lingwen on 2009-03-01
ctrl+del gives you a permanent delete which is more efficient than trash in my opinion

---

### Post by Paskinel on 2009-03-01
> **msrinath80 said:**
> There is a command called shred in GNU/Linux that does this.

```
shred filename
```

For more information try 'man shred'

-What is 'man shred'?
Any step-by-step instruction?
Just installed Ubuntu, and I'm new to LINUX...

---

### Post by mb_webguy on 2009-03-02
"man" is short for "manual", as in an instruction manual.  The man command gives provides the usage information about a command, such as a description of the command, it's syntax, and options.

---

### Post by radar2020 on 2009-03-02
To securely erase a file using shred  use the terminal.  APPLICATIONS > ACCESSORIES > TERMINAL
		
			Navigate to the directory where the file is located.  To shred a file called filename.xyz in Documents do this:
			ubuntu@ubuntucomputer:~$ cd Documents
			ubuntu@ubuntucomputer:~/Documents$ shred -uzvn N filename.xyz
			
				Where N is the number of shredding passes.

I don't think shred works on a folder if there are files in it.  Instead I use secure-delete .  This will make 38 passes.
	
	Ubuntu doesn't come with secure-delete installed.  Click on SYSTEM > ADMINISTRATION> 	SYNAPTIC PACKAGE MANAGER.  Search for secure-delete and install.

		Follow the same procedure in the terminal as above using these commands instead of shred.

			For File:   ```
 srm -v filename.xyz
```
			For Directory:   ```
srm -rv directoryname/
```

---

### Post by Andrew.Z on 2009-06-09
> **Paskinel said:**
> -How can I safely Erase/Delete Files and Folders?

-Is there any **Ubuntu** program (like Eraser in Wind-ow$...)
that uses Sefe Erase/Delete Overwriting Methods
(i.e. DoD-3, DoD-7, Guttman 35)?

[BleachBit 0.5.1 has secure file delete](http://bleachbit.blogspot.com/2009/06/bleachbit-051-released-file-shredder.html) from a nice convenient graphical interface, so you don't have to know the "shred" terminal command.  The web site has packages for the latest version of Ubuntu.

A future version will process whole folders; the current version lets you choose multiple files.

[Guttman 35 and similar algorithms generally give a false sense of security](http://bleachbit.blogspot.com/2009/06/validating-secure-erase.html) while wasting your time, so I recommend not using it unless your whole hard drive is smaller than 20GB (which is ancient by today's standards).

---

