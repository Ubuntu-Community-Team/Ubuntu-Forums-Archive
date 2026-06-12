---
title: "Installing Heroes of Might and Magic 3 on x86_64"
date: 2005-08-27
forum: Gaming &amp; Leisure
---

### Post by UrbanFallout on 2005-08-27
Hi everyone

I thought this may be useful to anyone out there who had difficulty installing Heroes of Might and Magic 3 (HOMM3) on an AMD 64 platform, because the install script kept quitting with the error message:
This installation doesn't support glibc-2.1 on x86_64

The error occurs because there are individual installer binaries for each architecture, stored in the directory structure on the CD. Of course only an "x86" subdirectory exists. The installer uses uname -m to check the architecture and then aborts when the "x86_64" directory is not found.

A simple work-around is to temporarily replace the uname binary with one that will output "x86". Here's how:

1. gedit ~/uname.cc
2. Paste following code into the file you're editing:

#include <iostream>

int main( int argc, char *argv[] )
{
	std::cout<<"x86\n";
	return 0;
}

3. save and exit
4. g++ ~/uname.cc -o ~/uname
5. sudo mv /bin/uname /bin/uname.bu
6. sudo cp ~/uname /bin/uname
7. Install HOMM3 using "sh setup.sh"
8. sudo mv /bin/uname.bu /bin/uname
9. rm ~/uname*
10. Enjoy...

This work around may help with other games.

Cheers
Nick

---

### Post by Harleen on 2005-08-27
You don't need to use a compiler, if a simple script can do the job. 
This:
```
echo "echo x86" > uname
chmod a+x uname
```
should do the same with less effort. If you put it in the bin/ folder in your home directory it will also be found before the original binary, so there's no need of messing around in the /bin directory.

---

### Post by Nachowarrior on 2007-09-15
Thanks for posting this I heart this game, and i've been looking around for a post like this for some time... i'm going to modify your original post to show how I got it to work. I've labeled them "extra:" to keep it simple


1. gedit ~/uname.cc
2. Paste following code into the file you're editing:

#include <iostream>

int main( int argc, char *argv[] )
{
std::cout<<"x86\n";
return 0;
}

3. save and exit
extra: sudo apt-get install g++
4. g++ ~/uname.cc -o ~/uname
5. sudo mv /bin/uname /bin/uname.bu
6. sudo cp ~/uname /bin/uname
7. extra: Install HOMM3 using "sudo bash setup.sh"
8. sudo mv /bin/uname.bu /bin/uname
9. rm ~/uname*
10. Enjoy...


the install folder should be /usr/local/games/heroes3
the icon repository is /usr/share/pixmaps

just chown the pixmaps folder and you should be able to paste any icons you want in it so you can create a shortcut.


And now just to figure out how to get the sound from being a bit choppy, and to get the thing to run fullscreen. :-p any ideas on that would be great!

---

### Post by ungalcrys on 2012-11-04
here is how i solved it:

i modified **setup.sh**

replaced
```
function DetectARCH {
	status=1
	case `uname -m` in
		i?86)  echo "x86"
			status=0;;
		*)     echo "`uname -m`"
			status=0;;
	esac
	return $status
}
```

with this:
```
function DetectARCH {
	status=1
	case `uname -m` in
		i?86)  echo "x86"
			status=0;;
		x86_64)  echo "x86"
			status=0;;
		*)     echo "`uname -m`"
			status=0;;
	esac
	return $status
}
```

---

