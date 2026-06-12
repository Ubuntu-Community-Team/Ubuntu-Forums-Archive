---
title: "[HELP] VMD 1.8.6 Installation on Lucid"
date: 2010-10-27
forum: Education &amp; Science
---

### Post by vergman on 2010-10-27
I'm having a hard time trying to install VMD on my machine.  

Claus7's post ([http://ubuntuforums.org/showthread.php?t=598518&highlight=vmd](http://ubuntuforums.org/showthread.php?t=598518&highlight=vmd)) has been very helpful, but my version of ubuntu is Lucid instead of Gutsy, and I'm wondering if I need something special to accomodate for it.

To attempt a 'fresh' reinstall, I have uninstalled csh using Synaptic, and have removed all other VMD files in my /usr/local directory.
I have modified the configure file as such:

##############################################################################
# User modifiable installation parameters, can be overridden by env variables
##############################################################################
# Name of shell script used to start program; this is the name used by users
$install_name = "vmd";

# Directory where VMD startup script is installed, should be in users' paths.
$install_bin_dir="/usr/home/michael/vmd-1.8.6/bin";

# Directory where VMD files and executables are installed
$install_library_dir="/usr/home/michael/vmd-1.8.6";


# optionally override hard-coded defaults above with environment variables
if ($ENV{VMDINSTALLNAME}) {
  $install_name = $ENV{VMDINSTALLNAME}
}
if ($ENV{VMDINSTALLBINDIR}) {
  $install_bin_dir = $ENV{VMDINSTALLBINDIR}
}
if ($ENV{VMDINSTALLLIBRARYDIR}) {
  $install_library_dir = $ENV{VMDINSTALLLIBRARYDIR}
}

##############################################################################

Where usr/home/michael/vmd-1.8.6 is where I extracted the tar file.

The following output is from my terminal:

michael@michael-laptop:~/vmd-1.8.6$ ls
Announcement  configure.options  doc      LINUXAMD64  proteins  scripts
bin           data               lib      msvc        python    shaders
configure     distrib            LICENSE  plugins     README    src
michael@michael-laptop:~/vmd-1.8.6$ ./configure
using configure.options: LINUXAMD64 OPENGL FLTK TK ACTC IMD SPACEBALL LIBTACHYON VRPN NETCDF TCL PYTHON PTHREADS NUMPY SILENT
michael@michael-laptop:~/vmd-1.8.6$ cd src
michael@michael-laptop:~/vmd-1.8.6/src$ sudo make install
Make sure /usr/home/michael/vmd-1.8.6/bin/vmd is in your path.
VMD installation complete.  Enjoy!
michael@michael-laptop:~/vmd-1.8.6/src$ cd /..
michael@michael-laptop:/$ ls

bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old

michael@michael-laptop:/$ cd /usr/home/michael/vmd-1.8.6/bin
michael@michael-laptop:/usr/home/michael/vmd-1.8.6/bin$ ls
vmd

michael@michael-laptop:/usr/home/michael/vmd-1.8.6/bin$ vmd

No command 'vmd' found, did you mean:
 Command 'wmd' from package 'wml' (universe)
 Command 'mmd' from package 'mtools' (main)
 Command 'vm' from package 'mgetty-voice' (universe)
 Command 'vgd' from package 'viewglob' (universe)
 Command 'pvmd' from package 'pvm' (universe)
vmd: command not found

michael@michael-laptop:/usr/home/michael/vmd-1.8.6/bin$ ./vmd
bash: ./vmd: /bin/csh: bad interpreter: No such file or directory

After I received the bash: ./vmd: /bin/csh: error, I re-installed the 'csh' from Synaptic, per Claus7, and attempted to run the file again, receiving the following output:

michael@michael-laptop:/usr/home/michael/vmd-1.8.6/bin$ ./vmd
bash: ./vmd: /bin/csh: bad interpreter: No such file or directory

michael@michael-laptop:/usr/home/michael/vmd-1.8.6/bin$ ./vmd
[1] 11363
michael@michael-laptop:/usr/home/michael/vmd-1.8.6/bin$ sudo ./vmd
[1] 11379

Any ideas? Are those numbers PID #'s? 

Note that Claus7' s original post recommends libstdc++5, which is no longer available on Synaptic.  Has it been replaced with libstdc++6, and if so, how what is my next move?  I do have libstdc++6, as well as 6-4.3 and 6-4.4.  

Please advise, 

Michael

---

### Post by Claus7 on 2011-03-31
Hello,

it has been a little while since you wrote this thread, yet now I came across it. Even a little bit late, I'll try to answer it.

So, first of it seems that Lucid was (is?) lacking the libstdc++5 library, which hardens the installation of vmd in that version of ubuntu. Yet, the developers of ubu noticed that and made a remedy to later versions, by including this library, even a little bit old, along with the latest versions. 

For this problem I would advice either an updated version of ubuntu or a manual installation of the library to lucid, which might be difficult for beginners.

About the installation of new versions of vmd, the process of installation is a little bit different, as I had described here for 32bit versions of ubuntu:
[http://ubuntuforums.org/showthread.php?t=1098590](http://ubuntuforums.org/showthread.php?t=1098590)

If you check out your message you will see:

> michael@michael-laptop:~/vmd-1.8.6$ ./configure
using configure.options: LINUXAMD64 OPENGL FLTK TK ACTC IMD SPACEBALL LIBTACHYON VRPN NETCDF TCL PYTHON PTHREADS NUMPY SILENT
michael@michael-laptop:~/vmd-1.8.6$ cd src
michael@michael-laptop:~/vmd-1.8.6/src$ sudo make install

that while typing ./configure, you have to give also an option of the available ones, which means that you have to type something like:
```
./configure LINUXAMD64
```
and then try to change directory to src.

Your installation might (will) not work if you do not solve the dependency issue of the aforementioned library, yet if you solve it, then you have to do the configuration with the procedure I already described.

So, even thought it says that the installation of vmd is ok and you can enjoy it, you have not installed vmd, that's why when you type ./vmd you get alternative options, as vmd is not recognised as a command.

Hope this helps in future notice,
Regards!

---

