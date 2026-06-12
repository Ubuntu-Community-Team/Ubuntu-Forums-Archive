---
title: "Pair-Programming using Screen, Vim and chroot"
date: 2009-06-03
forum: General Help
---

### Post by orengolan on 2009-06-03
I want to pair-program with a friend over the internet using vim.
My main user is oren and I created a user named guest for my friend.
I connect directly to my desktop (9.04) with the user oren, and I run screen.
my friend connects via ssh (guest user) and both of us are working on the same screen session with vim. life is great.
The steps to do it are here: [http://interblah.net/multi-user-gnu-screen](http://interblah.net/multi-user-gnu-screen).

I also want to make sure my friend can't harm my machine
so I use a script that can 'jail' my friend in it's own home folder -
[http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/](http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/)
I use the ubuntu version of this script, the last link on this page.
Here it is:

```
#!/bin/sh
#
# (c) Copyright by Wolfgang Fuschlberger
#
#    This program is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#    ( http://www.fsf.org/licenses/gpl.txt )
#####################################################################

# first Release: 2004-07-30
# CHB - 20080908 - hint for changes
RELEASE="2007-10-19 /modded: CHB-20080908"
#
# The latest version of the script is available at
#   http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/
#
# Feedback is welcome!
#
# Thanks for Bugfixes / Enhancements to 
# Michael Prokop <http://www.michael-prokop.at/chroot/>,
# Randy K., Randy D., Jonathan Hunter and everybody else.
#####################################################################

#
# Features:
# - enable scp and sftp in the chroot-jail
# - use one directory (default /home/jail/) as chroot for all users
# - create new accounts
# - move existing accounts to chroot
#####################################################################

# path to sshd's config file: needed for automatic detection of the locaten of
# the sftp-server binary
SSHD_CONFIG="/etc/ssh/sshd_config"

# Check if we are called with username or update
if [ -z "$1" ] ; then
  echo
  echo "ERROR: Parameter missing. Did you forget the username?"
  echo "-------------------------------------------------------------"
  echo
  echo "USAGE:"
  echo "Create new chrooted account or"
  echo "add existing User to chroot-jail:"
  echo "-> $0 username"
  echo
  echo "or specify \$SHELL and path where the jail should be located:"
  echo "-> $0 username [/path/to/chroot-shell [/path/to/jail]]"
  echo "Default shell       = /bin/chroot-shell"
  echo "Default chroot-path = /home/jail"
  echo "-------------------------------------------------------------"
  echo
  echo "Updating files in the chroot-jail:"
  echo "-> $0 update [/path/to/chroot-shell [/path/to/jail]]"
  echo "-------------------------------------------------------------"
  echo
  echo "To uninstall:"
  echo " # userdel \$USER"
  echo " # rm -rf /home/jail"
  echo " (this deletes all Users' files!)"
  echo " # rm -f /bin/chroot-shell"
  echo " manually delete the User's line from /etc/sudoers"
# CHB - 20080908 - hint because of some changes on ubuntu 8.04 and my needs :-)
  echo " WARNING!! SOME CHANGES TO FIT MY NEEDS ;-) /CHB"
  exit
fi

if [ -z "$PATH" ] ; then 
  PATH=/bin:/usr/bin:/usr/local/bin:/sbin:/usr/sbin
fi

echo
echo Release: $RELEASE
echo

echo "Am I root?  "
if [ "$(whoami &2>/dev/null)" != "root" ] && [ "$(id -un &2>/dev/null)" != "root" ] ; then
  echo "  NO!

Error: You must be root to run this script."
  exit 1
fi
echo "  OK";

# Check existence of necessary files
echo "Checking distribution... "
if [ -f /etc/debian_version ];
  then echo "  Supported Distribution found"
       echo "  System is running Debian Linux"
       DISTRO=DEBIAN;
elif [ -f /etc/SuSE-release ];
  then echo "  Supported Distribution found"
       echo "  System is running SuSE Linux"
       DISTRO=SUSE;
elif [ -f /etc/fedora-release ];
  then echo "  Supported Distribution found"
       echo "  System is running Fedora Linux"
       DISTRO=FEDORA;
elif [ -f /etc/redhat-release ];
  then echo "  Supported Distribution found"
       echo "  System is running Red Hat Linux"
       DISTRO=REDHAT;
else echo -e "  failed...........\nThis script works best on Debian, Red Hat, Fedora and SuSE Linux!\nLet's try it nevertheless....\nIf some program files cannot be found adjust the respective path in line 98\n"
#exit 1
fi

# Specify the apps you want to copy to the jail
if [ "$DISTRO" = SUSE ]; then
  APPS="/bin/bash /bin/cp /usr/bin/dircolors /bin/ls /bin/mkdir /bin/mv /bin/rm /bin/rmdir /bin/sh /bin/su /usr/bin/groups /usr/bin/id /usr/bin/netcat /usr/bin/rsync /usr/bin/ssh /usr/bin/scp /sbin/unix_chkpwd"
elif [ "$DISTRO" = FEDORA ]; then
  APPS="/bin/bash /bin/cp /usr/bin/dircolors /bin/ls /bin/mkdir /bin/mv /bin/rm /bin/rmdir /bin/sh /bin/su /usr/bin/groups /usr/bin/id /usr/bin/nc /usr/bin/rsync /usr/bin/ssh /usr/bin/scp /sbin/unix_chkpwd"
elif [ "$DISTRO" = REDHAT ]; then
  APPS="/bin/bash /bin/cp /usr/bin/dircolors /bin/ls /bin/mkdir /bin/mv /bin/rm /bin/rmdir /bin/sh /bin/su /usr/bin/groups /usr/bin/id /usr/bin/nc /usr/bin/rsync /usr/bin/ssh /usr/bin/scp /sbin/unix_chkpwd"
elif [ "$DISTRO" = DEBIAN ]; then
  APPS="/bin/bash /bin/cp /usr/bin/dircolors /bin/ls /bin/mkdir /bin/mv /bin/rm /bin/rmdir /bin/sh /bin/su /usr/bin/groups /usr/bin/id /usr/bin/rsync /usr/bin/ssh /usr/bin/scp /sbin/unix_chkpwd /usr/bin/screen"
else
  APPS="/bin/bash /bin/cp /usr/bin/dircolors /bin/ls /bin/mkdir /bin/mv /bin/rm /bin/rmdir /bin/sh /bin/su /usr/bin/groups /usr/bin/id /usr/bin/rsync /usr/bin/ssh /usr/bin/scp /usr/sbin/unix_chkpwd /usr/bin/screen"
fi

# Check existence of necessary files
echo "Checking for which... " 
#if [ -f $(which which) ] ;
# not good because if which does not exist I look for an 
# empty filename and get OK nevertheless
if ( test -f /usr/bin/which ) || ( test -f /bin/which ) || ( test -f /sbin/which ) || ( test -f /usr/sbin/which );
  then echo "  OK";
  else echo "  failed

Please install which-binary!
"
exit 1
fi

echo "Checking for chroot..." 
if [ `which chroot` ];
  then echo "  OK";
  else echo "  failed

chroot not found!
Please install chroot-package/binary!
"
exit 1
fi

echo "Checking for sudo..." 
if [ `which sudo` ]; then
  echo "  OK";
else 
  echo "  failed

sudo not found!
Please install sudo-package/binary!
"
exit 1
fi

echo "Checking for dirname..." 
if [ `which dirname` ]; then
  echo "  OK";
else 
  echo "  failed

dirname not found!
Please install dirname-binary (to be found eg in the package coreutils)!
"
exit 1
fi

echo "Checking for awk..." 
if [ `which awk` ]; then
  echo "  OK
";
else 
  echo "  failed

awk not found!
Please install (g)awk-package/binary!
"
exit 1
fi

# get location of sftp-server binary from /etc/ssh/sshd_config
# check for existence of /etc/ssh/sshd_config and for
# (uncommented) line with sftp-server filename. If neither exists, just skip
# this step and continue without sftp-server
#
#if  (test ! -f /etc/ssh/sshd_config &> /dev/null); then
#  echo "
#File /etc/ssh/sshd_config not found.
#Not checking for path to sftp-server.
#  ";
#else
if [ ! -f ${SSHD_CONFIG} ]
then
   echo "File ${SSHD_CONFIG} not found."
   echo "Not checking for path to sftp-server."
   echo "Please adjust the global \$SSHD_CONFIG variable"
else
  if !(grep -v "^#" ${SSHD_CONFIG} | grep -i sftp-server &> /dev/null); then
    echo "Obviously no sftp-server is running on this system.
";
  else SFTP_SERVER=$(grep -v "^#" ${SSHD_CONFIG} | grep -i sftp-server | awk  '{ print $3}')
  fi
fi

#if !(grep -v "^#" /etc/ssh/sshd_config | grep -i sftp-server /etc/ssh/sshd_config | awk  '{ print $3}' &> /dev/null); then
APPS="$APPS $SFTP_SERVER"

# Get accountname to create / move
CHROOT_USERNAME=$1

if ! [ -z "$2" ] ; then
  SHELL=$2
else
# CHB - 20080908 - changed default shell per user
#  SHELL=/bin/chroot-shell
  SHELL=/bin/chroot-shell-${CHROOT_USERNAME}
fi

if ! [ -z "$3" ] ; then
  JAILPATH=$3
else
# CHB - 20080908 - changed default jailpath per user
#  JAILPATH=/home/jail
  JAILPATH=/home/jail/${CHROOT_USERNAME}
fi

# Exit if user already exists
#id $CHROOT_USERNAME > /dev/null 2>&1 && { echo "User exists."; echo "Exiting."; exit 1; }

# Check if user already exists and ask for confirmation
# we have to trust that root knows what she is doing when saying 'yes'
if ( id $CHROOT_USERNAME > /dev/null 2>&1 ) ; then {
echo "
-----------------------------
User $CHROOT_USERNAME exists. 

Are you sure you want to modify the users home directory and lock him into the
chroot directory?
Are you REALLY sure?
Say only yes if you absolutely know what you are doing!"
  read -p "(yes/no) -> " MODIFYUSER
  if [ "$MODIFYUSER" != "yes" ]; then
    echo "
Not entered yes. Exiting...."
    exit 1
  fi
}
else
  CREATEUSER="yes"
fi

# Create $SHELL (shell for jailed accounts)
if [ -f ${SHELL} ] ; then
  echo "
-----------------------------
The file $SHELL exists. 
Probably it was created by this script.

Are you sure you want to overwrite it?
(you want to say yes for example if you are running the script for the second
time when adding more than one account to the jail)"
read -p "(yes/no) -> " OVERWRITE
if [ "$OVERWRITE" != "yes" ]; then
  echo "
Not entered yes. Exiting...."
  exit 1
fi
else
  echo "Creating $SHELL"
  echo '#!/bin/sh' > $SHELL
  echo "`which sudo` `which chroot` $JAILPATH /bin/su - \$USER" \"\$@\" >> $SHELL
  chmod 755 $SHELL
fi

# make common jail for everybody if inexistent
if [ ! -d ${JAILPATH} ] ; then
  mkdir -p ${JAILPATH}
  echo "Creating ${JAILPATH}"
fi
cd ${JAILPATH}

# Create directories in jail that do not exist yet
JAILDIRS="dev etc etc/pam.d bin home sbin usr usr/bin usr/lib"
for directory in $JAILDIRS ; do
  if [ ! -d "$JAILPATH/$directory" ] ; then
    mkdir $JAILPATH/"$directory"
    echo "Creating $JAILPATH/$directory"
  fi
done
echo

# Comment in the following lines if your apache can't read the directories and
# uses the security contexts
# Fix security contexts so Apache can read files
#CHCON=$(`which chcon`)
#if [ -n "$CHCON" ] && [ -x $CHCON ]; then
#    $CHCON -t home_root_t $JAILPATH/home
#    $CHCON -t user_home_dir_t $JAILPATH/home/$CHROOT_USERNAME
#fi

# Creating necessary devices
[ -r $JAILPATH/dev/urandom ] || mknod $JAILPATH/dev/urandom c 1 9
[ -r $JAILPATH/dev/null ]    || mknod -m 666 $JAILPATH/dev/null    c 1 3
[ -r $JAILPATH/dev/zero ]    || mknod -m 666 $JAILPATH/dev/zero    c 1 5
[ -r $JAILPATH/dev/tty ]     || mknod -m 666 $JAILPATH/dev/tty     c 5 0 

# if we only want to update the files in the jail
# skip the creation of the new account
if [ "$1" != "update" ]; then

# Modifiy /etc/sudoers to enable chroot-ing for users
# must be removed by hand if account is deleted
echo "Modifying /etc/sudoers"
echo "$CHROOT_USERNAME       ALL=NOPASSWD: `which chroot`, /bin/su - $CHROOT_USERNAME" >> /etc/sudoers

# Define HomeDir for simple referencing
HOMEDIR="$JAILPATH/home/$CHROOT_USERNAME"

# Create new account, setting $SHELL to the above created script and
# $HOME to $JAILPATH/home/*
if [ "$CREATEUSER" != "yes" ] ; then echo "
Not creating new User account
Modifying User \"$CHROOT_USERNAME\" 
Copying files in $CHROOT_USERNAME's \$HOME to \"$HOMEDIR\"
"
# CHB - 20080908 - changed default permission to home directory because of apache user directories
usermod -d "$HOMEDIR" -m -s "$SHELL" $CHROOT_USERNAME && chmod 701 "$HOMEDIR"
fi

if [ "$CREATEUSER" = "yes" ] ; then {
echo "Adding User \"$CHROOT_USERNAME\" to system"
# CHB - 20080908 - changed default permission to home directory because of apache user directories
useradd -m -d "$HOMEDIR" -s "$SHELL" $CHROOT_USERNAME && chmod 701 "$HOMEDIR"

# Enter password for new account
if !(passwd $CHROOT_USERNAME);
  then echo "Passwords are probably not the same, try again."
  exit 1;
fi
echo
}
fi

# Create /usr/bin/groups in the jail
echo "#!/bin/bash" > usr/bin/groups
echo "id -Gn" >> usr/bin/groups
chmod 755 usr/bin/groups

# Add users to etc/passwd
#
# check if file exists (ie we are not called for the first time)
# if yes skip root's entry and do not overwrite the file
if [ ! -f etc/passwd ] ; then
 grep /etc/passwd -e "^root" > ${JAILPATH}/etc/passwd
fi
if [ ! -f etc/group ] ; then
 grep /etc/group -e "^root" > ${JAILPATH}/etc/group
# add the group for all users to etc/group (otherwise there is a nasty error
# message and probably because of that changing directories doesn't work with
# winSCP)
 grep /etc/group -e "^users" >> ${JAILPATH}/etc/group
fi

# grep the username which was given to us from /etc/passwd and add it
# to ./etc/passwd replacing the $HOME with the directory as it will then 
# appear in the jail
echo "Adding User $CHROOT_USERNAME to jail"
grep -e "^$CHROOT_USERNAME:" /etc/passwd | \
 sed -e "s#$JAILPATH##"      \
     -e "s#$SHELL#/bin/bash#"  >> ${JAILPATH}/etc/passwd

# if the system uses one account/one group we write the
# account's group to etc/group
grep -e "^$CHROOT_USERNAME:" /etc/group >> ${JAILPATH}/etc/group

# write the user's line from /etc/shadow to /home/jail/etc/shadow
grep -e "^$CHROOT_USERNAME:" /etc/shadow >> ${JAILPATH}/etc/shadow
chmod 600 ${JAILPATH}/etc/shadow

# endif for =! update
fi

# Copy the apps and the related libs
echo "Copying necessary library-files to jail (may take some time)"

# The original code worked fine on RedHat 7.3, but did not on FC3.
# On FC3, when the 'ldd' is done, there is a 'linux-gate.so.1' that 
# points to nothing (or a 90xb.....), and it also does not pick up
# some files that start with a '/'. To fix this, I am doing the ldd
# to a file called ldlist, then going back into the file and pulling
# out the libs that start with '/'
# 
# Randy K.
#
# The original code worked fine on 2.4 kernel systems. Kernel 2.6
# introduced an internal library called 'linux-gate.so.1'. This 
# 'phantom' library caused non-critical errors to display during the 
# copy since the file does not actually exist on the file system. 
# To fix re-direct output of ldd to a file, parse the file and get 
# library files that start with /
#

# create temporary files with mktemp, if that doesn't work for some reason use
# the old method with $HOME/ldlist[2] (so I don't have to check the existence
# of the mktemp package / binary at the beginning
#


# CHB - 20080908 - because of some error msgs on ubuntu 8.04 two lines commented out and three lines new
#TMPFILE1=`mktemp` &> /dev/null ||  TMPFILE1="${HOME}/ldlist" ;  if [ -x ${TMPFILE1} ]; then mv ${TMPFILE1} ${TMPFILE1}.bak;fi
#TMPFILE2=`mktemp` &> /dev/null ||  TMPFILE2="${HOME}/ldlist2" ;  if [ -x ${TMPFILE2} ]; then mv ${TMPFILE2} ${TMPFILE2}.bak;fi
TMPFILE1="${HOME}/ldlist"
TMPFILE2="${HOME}/ldlist2"
touch $TMPFILE2

for app in $APPS;  do
    # First of all, check that this application exists
    if [ -x $app ]; then
        # Check that the directory exists; create it if not.
#        app_path=`echo $app | sed -e 's#\(.\+\)/[^/]\+#\1#'`
        app_path=`dirname $app`
        if ! [ -d .$app_path ]; then
            mkdir -p .$app_path
        fi

		# If the files in the chroot are on the same file system as the
		# original files you should be able to use hard links instead of
		# copying the files, too. Symbolic links cannot be used, because the
		# original files are outside the chroot.
		cp -p $app .$app

        # get list of necessary libraries
        ldd $app >> ${TMPFILE1}
    fi
done

# CHB - 20080908 - some errors in here on ubuntu 8.04... but works for now !
# Clear out any old temporary file before we start
for libs in `cat ${TMPFILE1}`; do
   frst_char="`echo $libs | cut -c1`"
   if [ "$frst_char" = "/" ]; then
     echo "$libs" >> ${TMPFILE2}
   fi
done

for lib in `cat ${TMPFILE2}`; do
    mkdir -p .`dirname $lib` > /dev/null 2>&1

	# If the files in the chroot are on the same file system as the original
	# files you should be able to use hard links instead of copying the files,
	# too. Symbolic links cannot be used, because the original files are
	# outside the chroot.
    cp $lib .$lib
done

#
# Now, cleanup the 2 files we created for the library list
#
#/bin/rm -f ${HOME}/ldlist
#/bin/rm -f ${HOME}/ldlist2
/bin/rm -f ${TMPFILE1}
/bin/rm -f ${TMPFILE2}

# Necessary files that are not listed by ldd.
#
# There might be errors because of files that do not exist but in the end it
# may work nevertheless (I added new file names at the end without deleting old
# ones for reasons of backward compatibility).
# So please test ssh/scp before reporting a bug.
if [ "$DISTRO" = SUSE ]; then
  cp /lib/libnss_compat.so.2 /lib/libnss_files.so.2 /lib/libnss_dns.so.2 /lib/libxcrypt.so.1 ${JAILPATH}/lib/
elif [ "$DISTRO" = FEDORA ]; then
  cp /lib/libnss_compat.so.2 /lib/libnsl.so.1 /lib/libnss_files.so.2 /lib/ld-linux.so.2 /lib/ld-ldb.so.3 /lib/ld-lsb.so.3 /lib/libnss_dns.so.2 /lib/libxcrypt.so.1 ${JAILPATH}/lib/
  cp /lib/*.* ${JAILPATH}/lib/
  cp /usr/lib/libcrack.so.2 ${JAILPATH}/usr/lib/
elif [ "$DISTRO" = REDHAT ]; then
  cp /lib/libnss_compat.so.2 /lib/libnsl.so.1 /lib/libnss_files.so.2 /lib/ld-linux.so.2 /lib/ld-lsb.so.1 /lib/libnss_dns.so.2 /lib/libxcrypt.so.1 ${JAILPATH}/lib/
  # needed for scp on RHEL
  echo "export LD_LIBRARY_PATH=/usr/kerberos/lib" >> ${JAILPATH}/etc/profile
elif [ "$DISTRO" = DEBIAN ]; then
  cp /lib/libnss_compat.so.2 /lib/libnsl.so.1 /lib/libnss_files.so.2 /lib/libcap.so.1 /lib/libnss_dns.so.2 ${JAILPATH}/lib/
else
  cp /lib/libnss_compat.so.2 /lib/libnsl.so.1 /lib/libnss_files.so.2 /lib/libcap.so.1 /lib/libnss_dns.so.2 ${JAILPATH}/lib/
fi

# if you are using a 64 bit system and have strange problems with login comment
# the following lines in, perhaps it works then (motto: if you can't find the
# needed library just copy all of them)
#
#cp /lib/*.* ${JAILPATH}/lib/
#cp /lib/lib64/*.* ${JAILPATH}/lib/lib64/ 

# if you are using PAM you need stuff from /etc/pam.d/ in the jail,
echo "Copying files from /etc/pam.d/ to jail"
cp /etc/pam.d/* ${JAILPATH}/etc/pam.d/

# ...and of course the PAM-modules...
echo "Copying PAM-Modules to jail"
cp -r /lib/security ${JAILPATH}/lib/

# ...and something else useful for PAM
cp -r /etc/security ${JAILPATH}/etc/
cp /etc/login.defs ${JAILPATH}/etc/

if [ -f /etc/DIR_COLORS ] ; then
  cp /etc/DIR_COLORS ${JAILPATH}/etc/
fi 

# Don't give more permissions than necessary
chown root.root ${JAILPATH}/bin/su
chmod 700 ${JAILPATH}/bin/su

exit

```

the script lets me choose what applications my friend will be able to run
so I added /usr/bin/screen to the script (the APPS variable).
I run the script: make_chroot_jail_mod.sh guest
and it creates /home/jail folder with all kind of stuff inside.
I can even see screen in /home/jail/guest/usr/bin.

but when I ssh as guest and type screen -ls oren/ I get: 

```
usr/bin/screen: 32: /usr/bin/select-screen-profile: not found

Your selected profile is not accessible.

Either select a different profile:
 $ select-screen-profile

Or install the extras package:
 $ sudo apt-get install screen-profiles-extras
```


Soliton from #screen (Thanks!) told me it's related to screen-profile and I can get rid of it.
I run this: sudo aptitude purge screen-profiles

now when I type /usr/bin/screen -ls oren/ i get:
```
Cannot identify account 'oren'.
```


I tried troubleshooting it by running this as the local user, oren: strace screen -R 2> output
here is the output file:

```
   1.
      execve("/usr/bin/screen", ["screen", "-R"], [/* 25 vars */]) = 0
   2.
      brk(0)                                  = 0x9628000
   3.
      fcntl64(0, F_GETFD)                     = 0
   4.
      fcntl64(1, F_GETFD)                     = 0
   5.
      fcntl64(2, F_GETFD)                     = 0
   6.
      access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
   7.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
   8.
      mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f5b000
   9.
      access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
  10.
      open("/etc/ld.so.cache", O_RDONLY)      = 3
  11.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=70733, ...}) = 0
  12.
      mmap2(NULL, 70733, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f49000
  13.
      close(3)                                = 0
  14.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
  15.
      open("/lib/libncursesw.so.5", O_RDONLY) = 3
  16.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\246\0\0004\0\0\0\350"..., 512) = 512
  17.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=248312, ...}) = 0
  18.
      mmap2(NULL, 252180, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f0b000
  19.
      mprotect(0xb7f45000, 4096, PROT_NONE)   = 0
  20.
      mmap2(0xb7f46000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3a) = 0xb7f46000
  21.
      close(3)                                = 0
  22.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
  23.
      open("/lib/tls/i686/cmov/libutil.so.1", O_RDONLY) = 3
  24.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\t\0\0004\0\0\0t"..., 512) = 512
  25.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=9684, ...}) = 0
  26.
      mmap2(NULL, 12424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f07000
  27.
      mmap2(0xb7f09000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7f09000
  28.
      close(3)                                = 0
  29.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
  30.
      open("/lib/tls/i686/cmov/libcrypt.so.1", O_RDONLY) = 3
  31.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \7\0\0004\0\0\0008"..., 512) = 512
  32.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=38296, ...}) = 0
  33.
      mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f06000
  34.
      mmap2(NULL, 201052, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ed4000
  35.
      mmap2(0xb7edd000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb7edd000
  36.
      mmap2(0xb7edf000, 155996, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7edf000
  37.
      close(3)                                = 0
  38.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
  39.
      open("/lib/libpam.so.0", O_RDONLY)      = 3
  40.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\31\0\0004\0\0\0\264"..., 512) = 512
  41.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=42476, ...}) = 0
  42.
      mmap2(NULL, 45260, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ec8000
  43.
      mmap2(0xb7ed2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xb7ed2000
  44.
      close(3)                                = 0
  45.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
  46.
      open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
  47.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320h\1\0004\0\0\0\344"..., 512) = 512
  48.
      fstat64(3, {st_mode=S_IFREG|0755, st_size=1442180, ...}) = 0
  49.
      mmap2(NULL, 1451632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d65000
  50.
      mprotect(0xb7ec1000, 4096, PROT_NONE)   = 0
  51.
      mmap2(0xb7ec2000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15c) = 0xb7ec2000
  52.
      mmap2(0xb7ec5000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7ec5000
  53.
      close(3)                                = 0
  54.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
  55.
      open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
  56.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \n\0\0004\0\0\0D"..., 512) = 512
  57.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=9676, ...}) = 0
  58.
      mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d61000
  59.
      mmap2(0xb7d63000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7d63000
  60.
      close(3)                                = 0
  61.
      mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d60000
  62.
      mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d5f000
  63.
      set_thread_area({entry_number:-1 -> 6, base_addr:0xb7d5f6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
  64.
      open("/dev/urandom", O_RDONLY)          = 3
  65.
      read(3, "P8\224\361"..., 4)             = 4
  66.
      close(3)                                = 0
  67.
      mprotect(0xb7d63000, 4096, PROT_READ)   = 0
  68.
      mprotect(0xb7ec2000, 8192, PROT_READ)   = 0
  69.
      mprotect(0xb7ed2000, 4096, PROT_READ)   = 0
  70.
      mprotect(0xb7edd000, 4096, PROT_READ)   = 0
  71.
      mprotect(0xb7f09000, 4096, PROT_READ)   = 0
  72.
      mprotect(0xb7f46000, 8192, PROT_READ)   = 0
  73.
      mprotect(0x8098000, 4096, PROT_READ)    = 0
  74.
      mprotect(0xb7f7a000, 4096, PROT_READ)   = 0
  75.
      munmap(0xb7f49000, 70733)               = 0
  76.
      getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
  77.
      close(1023)                             = -1 EBADF (Bad file descriptor)
  78.
      close(1022)                             = -1 EBADF (Bad file descriptor)
  79.
      close(1021)                             = -1 EBADF (Bad file descriptor)
  80.
      close(1020)                             = -1 EBADF (Bad file descriptor)
  81.
      close(1019)                             = -1 EBADF (Bad file descriptor)
  82.
      close(1018)                             = -1 EBADF (Bad file descriptor)
  83.
      close(1017)                             = -1 EBADF (Bad file descriptor)
  84.
      close(1016)                             = -1 EBADF (Bad file descriptor)
  85.
      close(1015)                             = -1 EBADF (Bad file descriptor)
  86.
      close(1014)                             = -1 EBADF (Bad file descriptor)
  87.
      close(1013)                             = -1 EBADF (Bad file descriptor)
  88.
      close(1012)                             = -1 EBADF (Bad file descriptor)
  89.
      close(1011)                             = -1 EBADF (Bad file descriptor)
  90.
      close(1010)                             = -1 EBADF (Bad file descriptor)
  91.
      close(1009)                             = -1 EBADF (Bad file descriptor)
  92.
      close(1008)                             = -1 EBADF (Bad file descriptor)
  93.
      close(1007)                             = -1 EBADF (Bad file descriptor)
  94.
      close(1006)                             = -1 EBADF (Bad file descriptor)
  95.
      close(1005)                             = -1 EBADF (Bad file descriptor)
  96.
      close(1004)                             = -1 EBADF (Bad file descriptor)
  97.
      close(1003)                             = -1 EBADF (Bad file descriptor)
  98.
      close(1002)                             = -1 EBADF (Bad file descriptor)
  99.
      close(1001)                             = -1 EBADF (Bad file descriptor)
 100.
      close(1000)                             = -1 EBADF (Bad file descriptor)
 101.
      close(999)                              = -1 EBADF (Bad file descriptor)
 102.
      close(998)                              = -1 EBADF (Bad file descriptor)
 103.
      close(997)                              = -1 EBADF (Bad file descriptor)
 104.
      close(996)                              = -1 EBADF (Bad file descriptor)
 105.
      close(995)                              = -1 EBADF (Bad file descriptor)
 106.
      close(994)                              = -1 EBADF (Bad file descriptor)
 107.
      close(993)                              = -1 EBADF (Bad file descriptor)
 108.
      close(992)                              = -1 EBADF (Bad file descriptor)
 109.
      close(991)                              = -1 EBADF (Bad file descriptor)
 110.
      close(990)                              = -1 EBADF (Bad file descriptor)
 111.
      close(989)                              = -1 EBADF (Bad file descriptor)
 112.
      close(988)                              = -1 EBADF (Bad file descriptor)
 113.
      close(987)                              = -1 EBADF (Bad file descriptor)
 114.
      close(986)                              = -1 EBADF (Bad file descriptor)
 115.
      close(985)                              = -1 EBADF (Bad file descriptor)
 116.
      close(984)                              = -1 EBADF (Bad file descriptor)
 117.
      close(983)                              = -1 EBADF (Bad file descriptor)
 118.
      close(982)                              = -1 EBADF (Bad file descriptor)
 119.
      close(981)                              = -1 EBADF (Bad file descriptor)
 120.
      close(980)                              = -1 EBADF (Bad file descriptor)
 121.
      close(979)                              = -1 EBADF (Bad file descriptor)
 122.
      close(978)                              = -1 EBADF (Bad file descriptor)
 123.
      close(977)                              = -1 EBADF (Bad file descriptor)
 124.
      close(976)                              = -1 EBADF (Bad file descriptor)
 125.
      close(975)                              = -1 EBADF (Bad file descriptor)
 126.
      close(974)                              = -1 EBADF (Bad file descriptor)
 127.
      close(973)                              = -1 EBADF (Bad file descriptor)
 128.
      close(972)                              = -1 EBADF (Bad file descriptor)
 129.
      close(971)                              = -1 EBADF (Bad file descriptor)
 130.
      close(970)                              = -1 EBADF (Bad file descriptor)
 131.
      close(969)                              = -1 EBADF (Bad file descriptor)
 132.
      close(968)                              = -1 EBADF (Bad file descriptor)
 133.
      close(967)                              = -1 EBADF (Bad file descriptor)
 134.
      close(966)                              = -1 EBADF (Bad file descriptor)
 135.
      close(965)                              = -1 EBADF (Bad file descriptor)
 136.
      close(964)                              = -1 EBADF (Bad file descriptor)
 137.
      close(963)                              = -1 EBADF (Bad file descriptor)
 138.
      close(962)                              = -1 EBADF (Bad file descriptor)
 139.
      close(961)                              = -1 EBADF (Bad file descriptor)
 140.
      close(960)                              = -1 EBADF (Bad file descriptor)
 141.
      close(959)                              = -1 EBADF (Bad file descriptor)
 142.
      close(958)                              = -1 EBADF (Bad file descriptor)
 143.
      close(957)                              = -1 EBADF (Bad file descriptor)
 144.
      close(956)                              = -1 EBADF (Bad file descriptor)
 145.
      close(955)                              = -1 EBADF (Bad file descriptor)
 146.
      close(954)                              = -1 EBADF (Bad file descriptor)
 147.
      close(953)                              = -1 EBADF (Bad file descriptor)
 148.
      close(952)                              = -1 EBADF (Bad file descriptor)
 149.
      close(951)                              = -1 EBADF (Bad file descriptor)
 150.
      close(950)                              = -1 EBADF (Bad file descriptor)
 151.
      close(949)                              = -1 EBADF (Bad file descriptor)
 152.
      close(948)                              = -1 EBADF (Bad file descriptor)
 153.
      close(947)                              = -1 EBADF (Bad file descriptor)
 154.
      close(946)                              = -1 EBADF (Bad file descriptor)
 155.
      close(945)                              = -1 EBADF (Bad file descriptor)
 156.
      close(944)                              = -1 EBADF (Bad file descriptor)
 157.
      close(943)                              = -1 EBADF (Bad file descriptor)
 158.
      close(942)                              = -1 EBADF (Bad file descriptor)
 159.
      close(941)                              = -1 EBADF (Bad file descriptor)
 160.
      close(940)                              = -1 EBADF (Bad file descriptor)
 161.
      close(939)                              = -1 EBADF (Bad file descriptor)
 162.
      close(938)                              = -1 EBADF (Bad file descriptor)
 163.
      close(937)                              = -1 EBADF (Bad file descriptor)
 164.
      close(936)                              = -1 EBADF (Bad file descriptor)
 165.
      close(935)                              = -1 EBADF (Bad file descriptor)
 166.
      close(934)                              = -1 EBADF (Bad file descriptor)
 167.
      close(933)                              = -1 EBADF (Bad file descriptor)
 168.
      close(932)                              = -1 EBADF (Bad file descriptor)
 169.
      close(931)                              = -1 EBADF (Bad file descriptor)
 170.
      close(930)                              = -1 EBADF (Bad file descriptor)
 171.
      close(929)                              = -1 EBADF (Bad file descriptor)
 172.
      close(928)                              = -1 EBADF (Bad file descriptor)
 173.
      close(927)                              = -1 EBADF (Bad file descriptor)
 174.
      close(926)                              = -1 EBADF (Bad file descriptor)
 175.
      close(925)                              = -1 EBADF (Bad file descriptor)
 176.
      close(924)                              = -1 EBADF (Bad file descriptor)
 177.
      close(923)                              = -1 EBADF (Bad file descriptor)
 178.
      close(922)                              = -1 EBADF (Bad file descriptor)
 179.
      close(921)                              = -1 EBADF (Bad file descriptor)
 180.
      close(920)                              = -1 EBADF (Bad file descriptor)
 181.
      close(919)                              = -1 EBADF (Bad file descriptor)
 182.
      close(918)                              = -1 EBADF (Bad file descriptor)
 183.
      close(917)                              = -1 EBADF (Bad file descriptor)
 184.
      close(916)                              = -1 EBADF (Bad file descriptor)
 185.
      close(915)                              = -1 EBADF (Bad file descriptor)
 186.
      close(914)                              = -1 EBADF (Bad file descriptor)
 187.
      close(913)                              = -1 EBADF (Bad file descriptor)
 188.
      close(912)                              = -1 EBADF (Bad file descriptor)
 189.
      close(911)                              = -1 EBADF (Bad file descriptor)
 190.
      close(910)                              = -1 EBADF (Bad file descriptor)
 191.
      close(909)                              = -1 EBADF (Bad file descriptor)
 192.
      close(908)                              = -1 EBADF (Bad file descriptor)
 193.
      close(907)                              = -1 EBADF (Bad file descriptor)
 194.
      close(906)                              = -1 EBADF (Bad file descriptor)
 195.
      close(905)                              = -1 EBADF (Bad file descriptor)
 196.
      close(904)                              = -1 EBADF (Bad file descriptor)
 197.
      close(903)                              = -1 EBADF (Bad file descriptor)
 198.
      close(902)                              = -1 EBADF (Bad file descriptor)
 199.
      close(901)                              = -1 EBADF (Bad file descriptor)
 200.
      close(900)                              = -1 EBADF (Bad file descriptor)
 201.
      close(899)                              = -1 EBADF (Bad file descriptor)
 202.
      close(898)                              = -1 EBADF (Bad file descriptor)
 203.
      close(897)                              = -1 EBADF (Bad file descriptor)
 204.
      close(896)                              = -1 EBADF (Bad file descriptor)
 205.
      close(895)                              = -1 EBADF (Bad file descriptor)
 206.
      close(894)                              = -1 EBADF (Bad file descriptor)
 207.
      close(893)                              = -1 EBADF (Bad file descriptor)
 208.
      close(892)                              = -1 EBADF (Bad file descriptor)
 209.
      close(891)                              = -1 EBADF (Bad file descriptor)
 210.
      close(890)                              = -1 EBADF (Bad file descriptor)
 211.
      close(889)                              = -1 EBADF (Bad file descriptor)
 212.
      close(888)                              = -1 EBADF (Bad file descriptor)
 213.
      close(887)                              = -1 EBADF (Bad file descriptor)
 214.
      close(886)                              = -1 EBADF (Bad file descriptor)
 215.
      close(885)                              = -1 EBADF (Bad file descriptor)
 216.
      close(884)                              = -1 EBADF (Bad file descriptor)
 217.
      close(883)                              = -1 EBADF (Bad file descriptor)
 218.
      close(882)                              = -1 EBADF (Bad file descriptor)
 219.
      close(881)                              = -1 EBADF (Bad file descriptor)
 220.
      close(880)                              = -1 EBADF (Bad file descriptor)
 221.
      close(879)                              = -1 EBADF (Bad file descriptor)
 222.
      close(878)                              = -1 EBADF (Bad file descriptor)
 223.
      close(877)                              = -1 EBADF (Bad file descriptor)
 224.
      close(876)                              = -1 EBADF (Bad file descriptor)
 225.
      close(875)                              = -1 EBADF (Bad file descriptor)
 226.
      close(874)                              = -1 EBADF (Bad file descriptor)
 227.
      close(873)                              = -1 EBADF (Bad file descriptor)
 228.
      close(872)                              = -1 EBADF (Bad file descriptor)
 229.
      close(871)                              = -1 EBADF (Bad file descriptor)
 230.
      close(870)                              = -1 EBADF (Bad file descriptor)
 231.
      close(869)                              = -1 EBADF (Bad file descriptor)
 232.
      close(868)                              = -1 EBADF (Bad file descriptor)
 233.
      close(867)                              = -1 EBADF (Bad file descriptor)
 234.
      close(866)                              = -1 EBADF (Bad file descriptor)
 235.
      close(865)                              = -1 EBADF (Bad file descriptor)
 236.
      close(864)                              = -1 EBADF (Bad file descriptor)
 237.
      close(863)                              = -1 EBADF (Bad file descriptor)
 238.
      close(862)                              = -1 EBADF (Bad file descriptor)
 239.
      close(861)                              = -1 EBADF (Bad file descriptor)
 240.
      close(860)                              = -1 EBADF (Bad file descriptor)
 241.
      close(859)                              = -1 EBADF (Bad file descriptor)
 242.
      close(858)                              = -1 EBADF (Bad file descriptor)
 243.
      close(857)                              = -1 EBADF (Bad file descriptor)
 244.
      close(856)                              = -1 EBADF (Bad file descriptor)
 245.
      close(855)                              = -1 EBADF (Bad file descriptor)
 246.
      close(854)                              = -1 EBADF (Bad file descriptor)
 247.
      close(853)                              = -1 EBADF (Bad file descriptor)
 248.
      close(852)                              = -1 EBADF (Bad file descriptor)
 249.
      close(851)                              = -1 EBADF (Bad file descriptor)
 250.
      close(850)                              = -1 EBADF (Bad file descriptor)
 251.
      close(849)                              = -1 EBADF (Bad file descriptor)
 252.
      close(848)                              = -1 EBADF (Bad file descriptor)
 253.
      close(847)                              = -1 EBADF (Bad file descriptor)
 254.
      close(846)                              = -1 EBADF (Bad file descriptor)
 255.
      close(845)                              = -1 EBADF (Bad file descriptor)
 256.
      close(844)                              = -1 EBADF (Bad file descriptor)
 257.
      close(843)                              = -1 EBADF (Bad file descriptor)
 258.
      close(842)                              = -1 EBADF (Bad file descriptor)
 259.
      close(841)                              = -1 EBADF (Bad file descriptor)
 260.
      close(840)                              = -1 EBADF (Bad file descriptor)
 261.
      close(839)                              = -1 EBADF (Bad file descriptor)
 262.
      close(838)                              = -1 EBADF (Bad file descriptor)
 263.
      close(837)                              = -1 EBADF (Bad file descriptor)
 264.
      close(836)                              = -1 EBADF (Bad file descriptor)
 265.
      close(835)                              = -1 EBADF (Bad file descriptor)
 266.
      close(834)                              = -1 EBADF (Bad file descriptor)
 267.
      close(833)                              = -1 EBADF (Bad file descriptor)
 268.
      close(832)                              = -1 EBADF (Bad file descriptor)
 269.
      close(831)                              = -1 EBADF (Bad file descriptor)
 270.
      close(830)                              = -1 EBADF (Bad file descriptor)
 271.
      close(829)                              = -1 EBADF (Bad file descriptor)
 272.
      close(828)                              = -1 EBADF (Bad file descriptor)
 273.
      close(827)                              = -1 EBADF (Bad file descriptor)
 274.
      close(826)                              = -1 EBADF (Bad file descriptor)
 275.
      close(825)                              = -1 EBADF (Bad file descriptor)
 276.
      close(824)                              = -1 EBADF (Bad file descriptor)
 277.
      close(823)                              = -1 EBADF (Bad file descriptor)
 278.
      close(822)                              = -1 EBADF (Bad file descriptor)
 279.
      close(821)                              = -1 EBADF (Bad file descriptor)
 280.
      close(820)                              = -1 EBADF (Bad file descriptor)
 281.
      close(819)                              = -1 EBADF (Bad file descriptor)
 282.
      close(818)                              = -1 EBADF (Bad file descriptor)
 283.
      close(817)                              = -1 EBADF (Bad file descriptor)
 284.
      close(816)                              = -1 EBADF (Bad file descriptor)
 285.
      close(815)                              = -1 EBADF (Bad file descriptor)
 286.
      close(814)                              = -1 EBADF (Bad file descriptor)
 287.
      close(813)                              = -1 EBADF (Bad file descriptor)
 288.
      close(812)                              = -1 EBADF (Bad file descriptor)
 289.
      close(811)                              = -1 EBADF (Bad file descriptor)
 290.
      close(810)                              = -1 EBADF (Bad file descriptor)
 291.
      close(809)                              = -1 EBADF (Bad file descriptor)
 292.
      close(808)                              = -1 EBADF (Bad file descriptor)
 293.
      close(807)                              = -1 EBADF (Bad file descriptor)
 294.
      close(806)                              = -1 EBADF (Bad file descriptor)
 295.
      close(805)                              = -1 EBADF (Bad file descriptor)
 296.
      close(804)                              = -1 EBADF (Bad file descriptor)
 297.
      close(803)                              = -1 EBADF (Bad file descriptor)
 298.
      close(802)                              = -1 EBADF (Bad file descriptor)
 299.
      close(801)                              = -1 EBADF (Bad file descriptor)
 300.
      close(800)                              = -1 EBADF (Bad file descriptor)
 301.
      close(799)                              = -1 EBADF (Bad file descriptor)
 302.
      close(798)                              = -1 EBADF (Bad file descriptor)
 303.
      close(797)                              = -1 EBADF (Bad file descriptor)
 304.
      close(796)                              = -1 EBADF (Bad file descriptor)
 305.
      close(795)                              = -1 EBADF (Bad file descriptor)
 306.
      close(794)                              = -1 EBADF (Bad file descriptor)
 307.
      close(793)                              = -1 EBADF (Bad file descriptor)
 308.
      close(792)                              = -1 EBADF (Bad file descriptor)
 309.
      close(791)                              = -1 EBADF (Bad file descriptor)
 310.
      close(790)                              = -1 EBADF (Bad file descriptor)
 311.
      close(789)                              = -1 EBADF (Bad file descriptor)
 312.
      close(788)                              = -1 EBADF (Bad file descriptor)
 313.
      close(787)                              = -1 EBADF (Bad file descriptor)
 314.
      close(786)                              = -1 EBADF (Bad file descriptor)
 315.
      close(785)                              = -1 EBADF (Bad file descriptor)
 316.
      close(784)                              = -1 EBADF (Bad file descriptor)
 317.
      close(783)                              = -1 EBADF (Bad file descriptor)
 318.
      close(782)                              = -1 EBADF (Bad file descriptor)
 319.
      close(781)                              = -1 EBADF (Bad file descriptor)
 320.
      close(780)                              = -1 EBADF (Bad file descriptor)
 321.
      close(779)                              = -1 EBADF (Bad file descriptor)
 322.
      close(778)                              = -1 EBADF (Bad file descriptor)
 323.
      close(777)                              = -1 EBADF (Bad file descriptor)
 324.
      close(776)                              = -1 EBADF (Bad file descriptor)
 325.
      close(775)                              = -1 EBADF (Bad file descriptor)
 326.
      close(774)                              = -1 EBADF (Bad file descriptor)
 327.
      close(773)                              = -1 EBADF (Bad file descriptor)
 328.
      close(772)                              = -1 EBADF (Bad file descriptor)
 329.
      close(771)                              = -1 EBADF (Bad file descriptor)
 330.
      close(770)                              = -1 EBADF (Bad file descriptor)
 331.
      close(769)                              = -1 EBADF (Bad file descriptor)
 332.
      close(768)                              = -1 EBADF (Bad file descriptor)
 333.
      close(767)                              = -1 EBADF (Bad file descriptor)
 334.
      close(766)                              = -1 EBADF (Bad file descriptor)
 335.
      close(765)                              = -1 EBADF (Bad file descriptor)
 336.
      close(764)                              = -1 EBADF (Bad file descriptor)
 337.
      close(763)                              = -1 EBADF (Bad file descriptor)
 338.
      close(762)                              = -1 EBADF (Bad file descriptor)
 339.
      close(761)                              = -1 EBADF (Bad file descriptor)
 340.
      close(760)                              = -1 EBADF (Bad file descriptor)
 341.
      close(759)                              = -1 EBADF (Bad file descriptor)
 342.
      close(758)                              = -1 EBADF (Bad file descriptor)
 343.
      close(757)                              = -1 EBADF (Bad file descriptor)
 344.
      close(756)                              = -1 EBADF (Bad file descriptor)
 345.
      close(755)                              = -1 EBADF (Bad file descriptor)
 346.
      close(754)                              = -1 EBADF (Bad file descriptor)
 347.
      close(753)                              = -1 EBADF (Bad file descriptor)
 348.
      close(752)                              = -1 EBADF (Bad file descriptor)
 349.
      close(751)                              = -1 EBADF (Bad file descriptor)
 350.
      close(750)                              = -1 EBADF (Bad file descriptor)
 351.
      close(749)                              = -1 EBADF (Bad file descriptor)
 352.
      close(748)                              = -1 EBADF (Bad file descriptor)
 353.
      close(747)                              = -1 EBADF (Bad file descriptor)
 354.
      close(746)                              = -1 EBADF (Bad file descriptor)
 355.
      close(745)                              = -1 EBADF (Bad file descriptor)
 356.
      close(744)                              = -1 EBADF (Bad file descriptor)
 357.
      close(743)                              = -1 EBADF (Bad file descriptor)
 358.
      close(742)                              = -1 EBADF (Bad file descriptor)
 359.
      close(741)                              = -1 EBADF (Bad file descriptor)
 360.
      close(740)                              = -1 EBADF (Bad file descriptor)
 361.
      close(739)                              = -1 EBADF (Bad file descriptor)
 362.
      close(738)                              = -1 EBADF (Bad file descriptor)
 363.
      close(737)                              = -1 EBADF (Bad file descriptor)
 364.
      close(736)                              = -1 EBADF (Bad file descriptor)
 365.
      close(735)                              = -1 EBADF (Bad file descriptor)
 366.
      close(734)                              = -1 EBADF (Bad file descriptor)
 367.
      close(733)                              = -1 EBADF (Bad file descriptor)
 368.
      close(732)                              = -1 EBADF (Bad file descriptor)
 369.
      close(731)                              = -1 EBADF (Bad file descriptor)
 370.
      close(730)                              = -1 EBADF (Bad file descriptor)
 371.
      close(729)                              = -1 EBADF (Bad file descriptor)
 372.
      close(728)                              = -1 EBADF (Bad file descriptor)
 373.
      close(727)                              = -1 EBADF (Bad file descriptor)
 374.
      close(726)                              = -1 EBADF (Bad file descriptor)
 375.
      close(725)                              = -1 EBADF (Bad file descriptor)
 376.
      close(724)                              = -1 EBADF (Bad file descriptor)
 377.
      close(723)                              = -1 EBADF (Bad file descriptor)
 378.
      close(722)                              = -1 EBADF (Bad file descriptor)
 379.
      close(721)                              = -1 EBADF (Bad file descriptor)
 380.
      close(720)                              = -1 EBADF (Bad file descriptor)
 381.
      close(719)                              = -1 EBADF (Bad file descriptor)
 382.
      close(718)                              = -1 EBADF (Bad file descriptor)
 383.
      close(717)                              = -1 EBADF (Bad file descriptor)
 384.
      close(716)                              = -1 EBADF (Bad file descriptor)
 385.
      close(715)                              = -1 EBADF (Bad file descriptor)
 386.
      close(714)                              = -1 EBADF (Bad file descriptor)
 387.
      close(713)                              = -1 EBADF (Bad file descriptor)
 388.
      close(712)                              = -1 EBADF (Bad file descriptor)
 389.
      close(711)                              = -1 EBADF (Bad file descriptor)
 390.
      close(710)                              = -1 EBADF (Bad file descriptor)
 391.
      close(709)                              = -1 EBADF (Bad file descriptor)
 392.
      close(708)                              = -1 EBADF (Bad file descriptor)
 393.
      close(707)                              = -1 EBADF (Bad file descriptor)
 394.
      close(706)                              = -1 EBADF (Bad file descriptor)
 395.
      close(705)                              = -1 EBADF (Bad file descriptor)
 396.
      close(704)                              = -1 EBADF (Bad file descriptor)
 397.
      close(703)                              = -1 EBADF (Bad file descriptor)
 398.
      close(702)                              = -1 EBADF (Bad file descriptor)
 399.
      close(701)                              = -1 EBADF (Bad file descriptor)
 400.
      close(700)                              = -1 EBADF (Bad file descriptor)
 401.
      close(699)                              = -1 EBADF (Bad file descriptor)
 402.
      close(698)                              = -1 EBADF (Bad file descriptor)
 403.
      close(697)                              = -1 EBADF (Bad file descriptor)
 404.
      close(696)                              = -1 EBADF (Bad file descriptor)
 405.
      close(695)                              = -1 EBADF (Bad file descriptor)
 406.
      close(694)                              = -1 EBADF (Bad file descriptor)
 407.
      close(693)                              = -1 EBADF (Bad file descriptor)
 408.
      close(692)                              = -1 EBADF (Bad file descriptor)
 409.
      close(691)                              = -1 EBADF (Bad file descriptor)
 410.
      close(690)                              = -1 EBADF (Bad file descriptor)
 411.
      close(689)                              = -1 EBADF (Bad file descriptor)
 412.
      close(688)                              = -1 EBADF (Bad file descriptor)
 413.
      close(687)                              = -1 EBADF (Bad file descriptor)
 414.
      close(686)                              = -1 EBADF (Bad file descriptor)
 415.
      close(685)                              = -1 EBADF (Bad file descriptor)
 416.
      close(684)                              = -1 EBADF (Bad file descriptor)
 417.
      close(683)                              = -1 EBADF (Bad file descriptor)
 418.
      close(682)                              = -1 EBADF (Bad file descriptor)
 419.
      close(681)                              = -1 EBADF (Bad file descriptor)
 420.
      close(680)                              = -1 EBADF (Bad file descriptor)
 421.
      close(679)                              = -1 EBADF (Bad file descriptor)
 422.
      close(678)                              = -1 EBADF (Bad file descriptor)
 423.
      close(677)                              = -1 EBADF (Bad file descriptor)
 424.
      close(676)                              = -1 EBADF (Bad file descriptor)
 425.
      close(675)                              = -1 EBADF (Bad file descriptor)
 426.
      close(674)                              = -1 EBADF (Bad file descriptor)
 427.
      close(673)                              = -1 EBADF (Bad file descriptor)
 428.
      close(672)                              = -1 EBADF (Bad file descriptor)
 429.
      close(671)                              = -1 EBADF (Bad file descriptor)
 430.
      close(670)                              = -1 EBADF (Bad file descriptor)
 431.
      close(669)                              = -1 EBADF (Bad file descriptor)
 432.
      close(668)                              = -1 EBADF (Bad file descriptor)
 433.
      close(667)                              = -1 EBADF (Bad file descriptor)
 434.
      close(666)                              = -1 EBADF (Bad file descriptor)
 435.
      close(665)                              = -1 EBADF (Bad file descriptor)
 436.
      close(664)                              = -1 EBADF (Bad file descriptor)
 437.
      close(663)                              = -1 EBADF (Bad file descriptor)
 438.
      close(662)                              = -1 EBADF (Bad file descriptor)
 439.
      close(661)                              = -1 EBADF (Bad file descriptor)
 440.
      close(660)                              = -1 EBADF (Bad file descriptor)
 441.
      close(659)                              = -1 EBADF (Bad file descriptor)
 442.
      close(658)                              = -1 EBADF (Bad file descriptor)
 443.
      close(657)                              = -1 EBADF (Bad file descriptor)
 444.
      close(656)                              = -1 EBADF (Bad file descriptor)
 445.
      close(655)                              = -1 EBADF (Bad file descriptor)
 446.
      close(654)                              = -1 EBADF (Bad file descriptor)
 447.
      close(653)                              = -1 EBADF (Bad file descriptor)
 448.
      close(652)                              = -1 EBADF (Bad file descriptor)
 449.
      close(651)                              = -1 EBADF (Bad file descriptor)
 450.
      close(650)                              = -1 EBADF (Bad file descriptor)
 451.
      close(649)                              = -1 EBADF (Bad file descriptor)
 452.
      close(648)                              = -1 EBADF (Bad file descriptor)
 453.
      close(647)                              = -1 EBADF (Bad file descriptor)
 454.
      close(646)                              = -1 EBADF (Bad file descriptor)
 455.
      close(645)                              = -1 EBADF (Bad file descriptor)
 456.
      close(644)                              = -1 EBADF (Bad file descriptor)
 457.
      close(643)                              = -1 EBADF (Bad file descriptor)
 458.
      close(642)                              = -1 EBADF (Bad file descriptor)
 459.
      close(641)                              = -1 EBADF (Bad file descriptor)
 460.
      close(640)                              = -1 EBADF (Bad file descriptor)
 461.
      close(639)                              = -1 EBADF (Bad file descriptor)
 462.
      close(638)                              = -1 EBADF (Bad file descriptor)
 463.
      close(637)                              = -1 EBADF (Bad file descriptor)
 464.
      close(636)                              = -1 EBADF (Bad file descriptor)
 465.
      close(635)                              = -1 EBADF (Bad file descriptor)
 466.
      close(634)                              = -1 EBADF (Bad file descriptor)
 467.
      close(633)                              = -1 EBADF (Bad file descriptor)
 468.
      close(632)                              = -1 EBADF (Bad file descriptor)
 469.
      close(631)                              = -1 EBADF (Bad file descriptor)
 470.
      close(630)                              = -1 EBADF (Bad file descriptor)
 471.
      close(629)                              = -1 EBADF (Bad file descriptor)
 472.
      close(628)                              = -1 EBADF (Bad file descriptor)
 473.
      close(627)                              = -1 EBADF (Bad file descriptor)
 474.
      close(626)                              = -1 EBADF (Bad file descriptor)
 475.
      close(625)                              = -1 EBADF (Bad file descriptor)
 476.
      close(624)                              = -1 EBADF (Bad file descriptor)
 477.
      close(623)                              = -1 EBADF (Bad file descriptor)
 478.
      close(622)                              = -1 EBADF (Bad file descriptor)
 479.
      close(621)                              = -1 EBADF (Bad file descriptor)
 480.
      close(620)                              = -1 EBADF (Bad file descriptor)
 481.
      close(619)                              = -1 EBADF (Bad file descriptor)
 482.
      close(618)                              = -1 EBADF (Bad file descriptor)
 483.
      close(617)                              = -1 EBADF (Bad file descriptor)
 484.
      close(616)                              = -1 EBADF (Bad file descriptor)
 485.
      close(615)                              = -1 EBADF (Bad file descriptor)
 486.
      close(614)                              = -1 EBADF (Bad file descriptor)
 487.
      close(613)                              = -1 EBADF (Bad file descriptor)
 488.
      close(612)                              = -1 EBADF (Bad file descriptor)
 489.
      close(611)                              = -1 EBADF (Bad file descriptor)
 490.
      close(610)                              = -1 EBADF (Bad file descriptor)
 491.
      close(609)                              = -1 EBADF (Bad file descriptor)
 492.
      close(608)                              = -1 EBADF (Bad file descriptor)
 493.
      close(607)                              = -1 EBADF (Bad file descriptor)
 494.
      close(606)                              = -1 EBADF (Bad file descriptor)
 495.
      close(605)                              = -1 EBADF (Bad file descriptor)
 496.
      close(604)                              = -1 EBADF (Bad file descriptor)
 497.
      close(603)                              = -1 EBADF (Bad file descriptor)
 498.
      close(602)                              = -1 EBADF (Bad file descriptor)
 499.
      close(601)                              = -1 EBADF (Bad file descriptor)
 500.
      close(600)                              = -1 EBADF (Bad file descriptor)
 501.
      close(599)                              = -1 EBADF (Bad file descriptor)
 502.
      close(598)                              = -1 EBADF (Bad file descriptor)
 503.
      close(597)                              = -1 EBADF (Bad file descriptor)
 504.
      close(596)                              = -1 EBADF (Bad file descriptor)
 505.
      close(595)                              = -1 EBADF (Bad file descriptor)
 506.
      close(594)                              = -1 EBADF (Bad file descriptor)
 507.
      close(593)                              = -1 EBADF (Bad file descriptor)
 508.
      close(592)                              = -1 EBADF (Bad file descriptor)
 509.
      close(591)                              = -1 EBADF (Bad file descriptor)
 510.
      close(590)                              = -1 EBADF (Bad file descriptor)
 511.
      close(589)                              = -1 EBADF (Bad file descriptor)
 512.
      close(588)                              = -1 EBADF (Bad file descriptor)
 513.
      close(587)                              = -1 EBADF (Bad file descriptor)
 514.
      close(586)                              = -1 EBADF (Bad file descriptor)
 515.
      close(585)                              = -1 EBADF (Bad file descriptor)
 516.
      close(584)                              = -1 EBADF (Bad file descriptor)
 517.
      close(583)                              = -1 EBADF (Bad file descriptor)
 518.
      close(582)                              = -1 EBADF (Bad file descriptor)
 519.
      close(581)                              = -1 EBADF (Bad file descriptor)
 520.
      close(580)                              = -1 EBADF (Bad file descriptor)
 521.
      close(579)                              = -1 EBADF (Bad file descriptor)
 522.
      close(578)                              = -1 EBADF (Bad file descriptor)
 523.
      close(577)                              = -1 EBADF (Bad file descriptor)
 524.
      close(576)                              = -1 EBADF (Bad file descriptor)
 525.
      close(575)                              = -1 EBADF (Bad file descriptor)
 526.
      close(574)                              = -1 EBADF (Bad file descriptor)
 527.
      close(573)                              = -1 EBADF (Bad file descriptor)
 528.
      close(572)                              = -1 EBADF (Bad file descriptor)
 529.
      close(571)                              = -1 EBADF (Bad file descriptor)
 530.
      close(570)                              = -1 EBADF (Bad file descriptor)
 531.
      close(569)                              = -1 EBADF (Bad file descriptor)
 532.
      close(568)                              = -1 EBADF (Bad file descriptor)
 533.
      close(567)                              = -1 EBADF (Bad file descriptor)
 534.
      close(566)                              = -1 EBADF (Bad file descriptor)
 535.
      close(565)                              = -1 EBADF (Bad file descriptor)
 536.
      close(564)                              = -1 EBADF (Bad file descriptor)
 537.
      close(563)                              = -1 EBADF (Bad file descriptor)
 538.
      close(562)                              = -1 EBADF (Bad file descriptor)
 539.
      close(561)                              = -1 EBADF (Bad file descriptor)
 540.
      close(560)                              = -1 EBADF (Bad file descriptor)
 541.
      close(559)                              = -1 EBADF (Bad file descriptor)
 542.
      close(558)                              = -1 EBADF (Bad file descriptor)
 543.
      close(557)                              = -1 EBADF (Bad file descriptor)
 544.
      close(556)                              = -1 EBADF (Bad file descriptor)
 545.
      close(555)                              = -1 EBADF (Bad file descriptor)
 546.
      close(554)                              = -1 EBADF (Bad file descriptor)
 547.
      close(553)                              = -1 EBADF (Bad file descriptor)
 548.
      close(552)                              = -1 EBADF (Bad file descriptor)
 549.
      close(551)                              = -1 EBADF (Bad file descriptor)
 550.
      close(550)                              = -1 EBADF (Bad file descriptor)
 551.
      close(549)                              = -1 EBADF (Bad file descriptor)
 552.
      close(548)                              = -1 EBADF (Bad file descriptor)
 553.
      close(547)                              = -1 EBADF (Bad file descriptor)
 554.
      close(546)                              = -1 EBADF (Bad file descriptor)
 555.
      close(545)                              = -1 EBADF (Bad file descriptor)
 556.
      close(544)                              = -1 EBADF (Bad file descriptor)
 557.
      close(543)                              = -1 EBADF (Bad file descriptor)
 558.
      close(542)                              = -1 EBADF (Bad file descriptor)
 559.
      close(541)                              = -1 EBADF (Bad file descriptor)
 560.
      close(540)                              = -1 EBADF (Bad file descriptor)
 561.
      close(539)                              = -1 EBADF (Bad file descriptor)
 562.
      close(538)                              = -1 EBADF (Bad file descriptor)
 563.
      close(537)                              = -1 EBADF (Bad file descriptor)
 564.
      close(536)                              = -1 EBADF (Bad file descriptor)
 565.
      close(535)                              = -1 EBADF (Bad file descriptor)
 566.
      close(534)                              = -1 EBADF (Bad file descriptor)
 567.
      close(533)                              = -1 EBADF (Bad file descriptor)
 568.
      close(532)                              = -1 EBADF (Bad file descriptor)
 569.
      close(531)                              = -1 EBADF (Bad file descriptor)
 570.
      close(530)                              = -1 EBADF (Bad file descriptor)
 571.
      close(529)                              = -1 EBADF (Bad file descriptor)
 572.
      close(528)                              = -1 EBADF (Bad file descriptor)
 573.
      close(527)                              = -1 EBADF (Bad file descriptor)
 574.
      close(526)                              = -1 EBADF (Bad file descriptor)
 575.
      close(525)                              = -1 EBADF (Bad file descriptor)
 576.
      close(524)                              = -1 EBADF (Bad file descriptor)
 577.
      close(523)                              = -1 EBADF (Bad file descriptor)
 578.
      close(522)                              = -1 EBADF (Bad file descriptor)
 579.
      close(521)                              = -1 EBADF (Bad file descriptor)
 580.
      close(520)                              = -1 EBADF (Bad file descriptor)
 581.
      close(519)                              = -1 EBADF (Bad file descriptor)
 582.
      close(518)                              = -1 EBADF (Bad file descriptor)
 583.
      close(517)                              = -1 EBADF (Bad file descriptor)
 584.
      close(516)                              = -1 EBADF (Bad file descriptor)
 585.
      close(515)                              = -1 EBADF (Bad file descriptor)
 586.
      close(514)                              = -1 EBADF (Bad file descriptor)
 587.
      close(513)                              = -1 EBADF (Bad file descriptor)
 588.
      close(512)                              = -1 EBADF (Bad file descriptor)
 589.
      close(511)                              = -1 EBADF (Bad file descriptor)
 590.
      close(510)                              = -1 EBADF (Bad file descriptor)
 591.
      close(509)                              = -1 EBADF (Bad file descriptor)
 592.
      close(508)                              = -1 EBADF (Bad file descriptor)
 593.
      close(507)                              = -1 EBADF (Bad file descriptor)
 594.
      close(506)                              = -1 EBADF (Bad file descriptor)
 595.
      close(505)                              = -1 EBADF (Bad file descriptor)
 596.
      close(504)                              = -1 EBADF (Bad file descriptor)
 597.
      close(503)                              = -1 EBADF (Bad file descriptor)
 598.
      close(502)                              = -1 EBADF (Bad file descriptor)
 599.
      close(501)                              = -1 EBADF (Bad file descriptor)
 600.
      close(500)                              = -1 EBADF (Bad file descriptor)
 601.
      close(499)                              = -1 EBADF (Bad file descriptor)
 602.
      close(498)                              = -1 EBADF (Bad file descriptor)
 603.
      close(497)                              = -1 EBADF (Bad file descriptor)
 604.
      close(496)                              = -1 EBADF (Bad file descriptor)
 605.
      close(495)                              = -1 EBADF (Bad file descriptor)
 606.
      close(494)                              = -1 EBADF (Bad file descriptor)
 607.
      close(493)                              = -1 EBADF (Bad file descriptor)
 608.
      close(492)                              = -1 EBADF (Bad file descriptor)
 609.
      close(491)                              = -1 EBADF (Bad file descriptor)
 610.
      close(490)                              = -1 EBADF (Bad file descriptor)
 611.
      close(489)                              = -1 EBADF (Bad file descriptor)
 612.
      close(488)                              = -1 EBADF (Bad file descriptor)
 613.
      close(487)                              = -1 EBADF (Bad file descriptor)
 614.
      close(486)                              = -1 EBADF (Bad file descriptor)
 615.
      close(485)                              = -1 EBADF (Bad file descriptor)
 616.
      close(484)                              = -1 EBADF (Bad file descriptor)
 617.
      close(483)                              = -1 EBADF (Bad file descriptor)
 618.
      close(482)                              = -1 EBADF (Bad file descriptor)
 619.
      close(481)                              = -1 EBADF (Bad file descriptor)
 620.
      close(480)                              = -1 EBADF (Bad file descriptor)
 621.
      close(479)                              = -1 EBADF (Bad file descriptor)
 622.
      close(478)                              = -1 EBADF (Bad file descriptor)
 623.
      close(477)                              = -1 EBADF (Bad file descriptor)
 624.
      close(476)                              = -1 EBADF (Bad file descriptor)
 625.
      close(475)                              = -1 EBADF (Bad file descriptor)
 626.
      close(474)                              = -1 EBADF (Bad file descriptor)
 627.
      close(473)                              = -1 EBADF (Bad file descriptor)
 628.
      close(472)                              = -1 EBADF (Bad file descriptor)
 629.
      close(471)                              = -1 EBADF (Bad file descriptor)
 630.
      close(470)                              = -1 EBADF (Bad file descriptor)
 631.
      close(469)                              = -1 EBADF (Bad file descriptor)
 632.
      close(468)                              = -1 EBADF (Bad file descriptor)
 633.
      close(467)                              = -1 EBADF (Bad file descriptor)
 634.
      close(466)                              = -1 EBADF (Bad file descriptor)
 635.
      close(465)                              = -1 EBADF (Bad file descriptor)
 636.
      close(464)                              = -1 EBADF (Bad file descriptor)
 637.
      close(463)                              = -1 EBADF (Bad file descriptor)
 638.
      close(462)                              = -1 EBADF (Bad file descriptor)
 639.
      close(461)                              = -1 EBADF (Bad file descriptor)
 640.
      close(460)                              = -1 EBADF (Bad file descriptor)
 641.
      close(459)                              = -1 EBADF (Bad file descriptor)
 642.
      close(458)                              = -1 EBADF (Bad file descriptor)
 643.
      close(457)                              = -1 EBADF (Bad file descriptor)
 644.
      close(456)                              = -1 EBADF (Bad file descriptor)
 645.
      close(455)                              = -1 EBADF (Bad file descriptor)
 646.
      close(454)                              = -1 EBADF (Bad file descriptor)
 647.
      close(453)                              = -1 EBADF (Bad file descriptor)
 648.
      close(452)                              = -1 EBADF (Bad file descriptor)
 649.
      close(451)                              = -1 EBADF (Bad file descriptor)
 650.
      close(450)                              = -1 EBADF (Bad file descriptor)
 651.
      close(449)                              = -1 EBADF (Bad file descriptor)
 652.
      close(448)                              = -1 EBADF (Bad file descriptor)
 653.
      close(447)                              = -1 EBADF (Bad file descriptor)
 654.
      close(446)                              = -1 EBADF (Bad file descriptor)
 655.
      close(445)                              = -1 EBADF (Bad file descriptor)
 656.
      close(444)                              = -1 EBADF (Bad file descriptor)
 657.
      close(443)                              = -1 EBADF (Bad file descriptor)
 658.
      close(442)                              = -1 EBADF (Bad file descriptor)
 659.
      close(441)                              = -1 EBADF (Bad file descriptor)
 660.
      close(440)                              = -1 EBADF (Bad file descriptor)
 661.
      close(439)                              = -1 EBADF (Bad file descriptor)
 662.
      close(438)                              = -1 EBADF (Bad file descriptor)
 663.
      close(437)                              = -1 EBADF (Bad file descriptor)
 664.
      close(436)                              = -1 EBADF (Bad file descriptor)
 665.
      close(435)                              = -1 EBADF (Bad file descriptor)
 666.
      close(434)                              = -1 EBADF (Bad file descriptor)
 667.
      close(433)                              = -1 EBADF (Bad file descriptor)
 668.
      close(432)                              = -1 EBADF (Bad file descriptor)
 669.
      close(431)                              = -1 EBADF (Bad file descriptor)
 670.
      close(430)                              = -1 EBADF (Bad file descriptor)
 671.
      close(429)                              = -1 EBADF (Bad file descriptor)
 672.
      close(428)                              = -1 EBADF (Bad file descriptor)
 673.
      close(427)                              = -1 EBADF (Bad file descriptor)
 674.
      close(426)                              = -1 EBADF (Bad file descriptor)
 675.
      close(425)                              = -1 EBADF (Bad file descriptor)
 676.
      close(424)                              = -1 EBADF (Bad file descriptor)
 677.
      close(423)                              = -1 EBADF (Bad file descriptor)
 678.
      close(422)                              = -1 EBADF (Bad file descriptor)
 679.
      close(421)                              = -1 EBADF (Bad file descriptor)
 680.
      close(420)                              = -1 EBADF (Bad file descriptor)
 681.
      close(419)                              = -1 EBADF (Bad file descriptor)
 682.
      close(418)                              = -1 EBADF (Bad file descriptor)
 683.
      close(417)                              = -1 EBADF (Bad file descriptor)
 684.
      close(416)                              = -1 EBADF (Bad file descriptor)
 685.
      close(415)                              = -1 EBADF (Bad file descriptor)
 686.
      close(414)                              = -1 EBADF (Bad file descriptor)
 687.
      close(413)                              = -1 EBADF (Bad file descriptor)
 688.
      close(412)                              = -1 EBADF (Bad file descriptor)
 689.
      close(411)                              = -1 EBADF (Bad file descriptor)
 690.
      close(410)                              = -1 EBADF (Bad file descriptor)
 691.
      close(409)                              = -1 EBADF (Bad file descriptor)
 692.
      close(408)                              = -1 EBADF (Bad file descriptor)
 693.
      close(407)                              = -1 EBADF (Bad file descriptor)
 694.
      close(406)                              = -1 EBADF (Bad file descriptor)
 695.
      close(405)                              = -1 EBADF (Bad file descriptor)
 696.
      close(404)                              = -1 EBADF (Bad file descriptor)
 697.
      close(403)                              = -1 EBADF (Bad file descriptor)
 698.
      close(402)                              = -1 EBADF (Bad file descriptor)
 699.
      close(401)                              = -1 EBADF (Bad file descriptor)
 700.
      close(400)                              = -1 EBADF (Bad file descriptor)
 701.
      close(399)                              = -1 EBADF (Bad file descriptor)
 702.
      close(398)                              = -1 EBADF (Bad file descriptor)
 703.
      close(397)                              = -1 EBADF (Bad file descriptor)
 704.
      close(396)                              = -1 EBADF (Bad file descriptor)
 705.
      close(395)                              = -1 EBADF (Bad file descriptor)
 706.
      close(394)                              = -1 EBADF (Bad file descriptor)
 707.
      close(393)                              = -1 EBADF (Bad file descriptor)
 708.
      close(392)                              = -1 EBADF (Bad file descriptor)
 709.
      close(391)                              = -1 EBADF (Bad file descriptor)
 710.
      close(390)                              = -1 EBADF (Bad file descriptor)
 711.
      close(389)                              = -1 EBADF (Bad file descriptor)
 712.
      close(388)                              = -1 EBADF (Bad file descriptor)
 713.
      close(387)                              = -1 EBADF (Bad file descriptor)
 714.
      close(386)                              = -1 EBADF (Bad file descriptor)
 715.
      close(385)                              = -1 EBADF (Bad file descriptor)
 716.
      close(384)                              = -1 EBADF (Bad file descriptor)
 717.
      close(383)                              = -1 EBADF (Bad file descriptor)
 718.
      close(382)                              = -1 EBADF (Bad file descriptor)
 719.
      close(381)                              = -1 EBADF (Bad file descriptor)
 720.
      close(380)                              = -1 EBADF (Bad file descriptor)
 721.
      close(379)                              = -1 EBADF (Bad file descriptor)
 722.
      close(378)                              = -1 EBADF (Bad file descriptor)
 723.
      close(377)                              = -1 EBADF (Bad file descriptor)
 724.
      close(376)                              = -1 EBADF (Bad file descriptor)
 725.
      close(375)                              = -1 EBADF (Bad file descriptor)
 726.
      close(374)                              = -1 EBADF (Bad file descriptor)
 727.
      close(373)                              = -1 EBADF (Bad file descriptor)
 728.
      close(372)                              = -1 EBADF (Bad file descriptor)
 729.
      close(371)                              = -1 EBADF (Bad file descriptor)
 730.
      close(370)                              = -1 EBADF (Bad file descriptor)
 731.
      close(369)                              = -1 EBADF (Bad file descriptor)
 732.
      close(368)                              = -1 EBADF (Bad file descriptor)
 733.
      close(367)                              = -1 EBADF (Bad file descriptor)
 734.
      close(366)                              = -1 EBADF (Bad file descriptor)
 735.
      close(365)                              = -1 EBADF (Bad file descriptor)
 736.
      close(364)                              = -1 EBADF (Bad file descriptor)
 737.
      close(363)                              = -1 EBADF (Bad file descriptor)
 738.
      close(362)                              = -1 EBADF (Bad file descriptor)
 739.
      close(361)                              = -1 EBADF (Bad file descriptor)
 740.
      close(360)                              = -1 EBADF (Bad file descriptor)
 741.
      close(359)                              = -1 EBADF (Bad file descriptor)
 742.
      close(358)                              = -1 EBADF (Bad file descriptor)
 743.
      close(357)                              = -1 EBADF (Bad file descriptor)
 744.
      close(356)                              = -1 EBADF (Bad file descriptor)
 745.
      close(355)                              = -1 EBADF (Bad file descriptor)
 746.
      close(354)                              = -1 EBADF (Bad file descriptor)
 747.
      close(353)                              = -1 EBADF (Bad file descriptor)
 748.
      close(352)                              = -1 EBADF (Bad file descriptor)
 749.
      close(351)                              = -1 EBADF (Bad file descriptor)
 750.
      close(350)                              = -1 EBADF (Bad file descriptor)
 751.
      close(349)                              = -1 EBADF (Bad file descriptor)
 752.
      close(348)                              = -1 EBADF (Bad file descriptor)
 753.
      close(347)                              = -1 EBADF (Bad file descriptor)
 754.
      close(346)                              = -1 EBADF (Bad file descriptor)
 755.
      close(345)                              = -1 EBADF (Bad file descriptor)
 756.
      close(344)                              = -1 EBADF (Bad file descriptor)
 757.
      close(343)                              = -1 EBADF (Bad file descriptor)
 758.
      close(342)                              = -1 EBADF (Bad file descriptor)
 759.
      close(341)                              = -1 EBADF (Bad file descriptor)
 760.
      close(340)                              = -1 EBADF (Bad file descriptor)
 761.
      close(339)                              = -1 EBADF (Bad file descriptor)
 762.
      close(338)                              = -1 EBADF (Bad file descriptor)
 763.
      close(337)                              = -1 EBADF (Bad file descriptor)
 764.
      close(336)                              = -1 EBADF (Bad file descriptor)
 765.
      close(335)                              = -1 EBADF (Bad file descriptor)
 766.
      close(334)                              = -1 EBADF (Bad file descriptor)
 767.
      close(333)                              = -1 EBADF (Bad file descriptor)
 768.
      close(332)                              = -1 EBADF (Bad file descriptor)
 769.
      close(331)                              = -1 EBADF (Bad file descriptor)
 770.
      close(330)                              = -1 EBADF (Bad file descriptor)
 771.
      close(329)                              = -1 EBADF (Bad file descriptor)
 772.
      close(328)                              = -1 EBADF (Bad file descriptor)
 773.
      close(327)                              = -1 EBADF (Bad file descriptor)
 774.
      close(326)                              = -1 EBADF (Bad file descriptor)
 775.
      close(325)                              = -1 EBADF (Bad file descriptor)
 776.
      close(324)                              = -1 EBADF (Bad file descriptor)
 777.
      close(323)                              = -1 EBADF (Bad file descriptor)
 778.
      close(322)                              = -1 EBADF (Bad file descriptor)
 779.
      close(321)                              = -1 EBADF (Bad file descriptor)
 780.
      close(320)                              = -1 EBADF (Bad file descriptor)
 781.
      close(319)                              = -1 EBADF (Bad file descriptor)
 782.
      close(318)                              = -1 EBADF (Bad file descriptor)
 783.
      close(317)                              = -1 EBADF (Bad file descriptor)
 784.
      close(316)                              = -1 EBADF (Bad file descriptor)
 785.
      close(315)                              = -1 EBADF (Bad file descriptor)
 786.
      close(314)                              = -1 EBADF (Bad file descriptor)
 787.
      close(313)                              = -1 EBADF (Bad file descriptor)
 788.
      close(312)                              = -1 EBADF (Bad file descriptor)
 789.
      close(311)                              = -1 EBADF (Bad file descriptor)
 790.
      close(310)                              = -1 EBADF (Bad file descriptor)
 791.
      close(309)                              = -1 EBADF (Bad file descriptor)
 792.
      close(308)                              = -1 EBADF (Bad file descriptor)
 793.
      close(307)                              = -1 EBADF (Bad file descriptor)
 794.
      close(306)                              = -1 EBADF (Bad file descriptor)
 795.
      close(305)                              = -1 EBADF (Bad file descriptor)
 796.
      close(304)                              = -1 EBADF (Bad file descriptor)
 797.
      close(303)                              = -1 EBADF (Bad file descriptor)
 798.
      close(302)                              = -1 EBADF (Bad file descriptor)
 799.
      close(301)                              = -1 EBADF (Bad file descriptor)
 800.
      close(300)                              = -1 EBADF (Bad file descriptor)
 801.
      close(299)                              = -1 EBADF (Bad file descriptor)
 802.
      close(298)                              = -1 EBADF (Bad file descriptor)
 803.
      close(297)                              = -1 EBADF (Bad file descriptor)
 804.
      close(296)                              = -1 EBADF (Bad file descriptor)
 805.
      close(295)                              = -1 EBADF (Bad file descriptor)
 806.
      close(294)                              = -1 EBADF (Bad file descriptor)
 807.
      close(293)                              = -1 EBADF (Bad file descriptor)
 808.
      close(292)                              = -1 EBADF (Bad file descriptor)
 809.
      close(291)                              = -1 EBADF (Bad file descriptor)
 810.
      close(290)                              = -1 EBADF (Bad file descriptor)
 811.
      close(289)                              = -1 EBADF (Bad file descriptor)
 812.
      close(288)                              = -1 EBADF (Bad file descriptor)
 813.
      close(287)                              = -1 EBADF (Bad file descriptor)
 814.
      close(286)                              = -1 EBADF (Bad file descriptor)
 815.
      close(285)                              = -1 EBADF (Bad file descriptor)
 816.
      close(284)                              = -1 EBADF (Bad file descriptor)
 817.
      close(283)                              = -1 EBADF (Bad file descriptor)
 818.
      close(282)                              = -1 EBADF (Bad file descriptor)
 819.
      close(281)                              = -1 EBADF (Bad file descriptor)
 820.
      close(280)                              = -1 EBADF (Bad file descriptor)
 821.
      close(279)                              = -1 EBADF (Bad file descriptor)
 822.
      close(278)                              = -1 EBADF (Bad file descriptor)
 823.
      close(277)                              = -1 EBADF (Bad file descriptor)
 824.
      close(276)                              = -1 EBADF (Bad file descriptor)
 825.
      close(275)                              = -1 EBADF (Bad file descriptor)
 826.
      close(274)                              = -1 EBADF (Bad file descriptor)
 827.
      close(273)                              = -1 EBADF (Bad file descriptor)
 828.
      close(272)                              = -1 EBADF (Bad file descriptor)
 829.
      close(271)                              = -1 EBADF (Bad file descriptor)
 830.
      close(270)                              = -1 EBADF (Bad file descriptor)
 831.
      close(269)                              = -1 EBADF (Bad file descriptor)
 832.
      close(268)                              = -1 EBADF (Bad file descriptor)
 833.
      close(267)                              = -1 EBADF (Bad file descriptor)
 834.
      close(266)                              = -1 EBADF (Bad file descriptor)
 835.
      close(265)                              = -1 EBADF (Bad file descriptor)
 836.
      close(264)                              = -1 EBADF (Bad file descriptor)
 837.
      close(263)                              = -1 EBADF (Bad file descriptor)
 838.
      close(262)                              = -1 EBADF (Bad file descriptor)
 839.
      close(261)                              = -1 EBADF (Bad file descriptor)
 840.
      close(260)                              = -1 EBADF (Bad file descriptor)
 841.
      close(259)                              = -1 EBADF (Bad file descriptor)
 842.
      close(258)                              = -1 EBADF (Bad file descriptor)
 843.
      close(257)                              = -1 EBADF (Bad file descriptor)
 844.
      close(256)                              = -1 EBADF (Bad file descriptor)
 845.
      close(255)                              = -1 EBADF (Bad file descriptor)
 846.
      close(254)                              = -1 EBADF (Bad file descriptor)
 847.
      close(253)                              = -1 EBADF (Bad file descriptor)
 848.
      close(252)                              = -1 EBADF (Bad file descriptor)
 849.
      close(251)                              = -1 EBADF (Bad file descriptor)
 850.
      close(250)                              = -1 EBADF (Bad file descriptor)
 851.
      close(249)                              = -1 EBADF (Bad file descriptor)
 852.
      close(248)                              = -1 EBADF (Bad file descriptor)
 853.
      close(247)                              = -1 EBADF (Bad file descriptor)
 854.
      close(246)                              = -1 EBADF (Bad file descriptor)
 855.
      close(245)                              = -1 EBADF (Bad file descriptor)
 856.
      close(244)                              = -1 EBADF (Bad file descriptor)
 857.
      close(243)                              = -1 EBADF (Bad file descriptor)
 858.
      close(242)                              = -1 EBADF (Bad file descriptor)
 859.
      close(241)                              = -1 EBADF (Bad file descriptor)
 860.
      close(240)                              = -1 EBADF (Bad file descriptor)
 861.
      close(239)                              = -1 EBADF (Bad file descriptor)
 862.
      close(238)                              = -1 EBADF (Bad file descriptor)
 863.
      close(237)                              = -1 EBADF (Bad file descriptor)
 864.
      close(236)                              = -1 EBADF (Bad file descriptor)
 865.
      close(235)                              = -1 EBADF (Bad file descriptor)
 866.
      close(234)                              = -1 EBADF (Bad file descriptor)
 867.
      close(233)                              = -1 EBADF (Bad file descriptor)
 868.
      close(232)                              = -1 EBADF (Bad file descriptor)
 869.
      close(231)                              = -1 EBADF (Bad file descriptor)
 870.
      close(230)                              = -1 EBADF (Bad file descriptor)
 871.
      close(229)                              = -1 EBADF (Bad file descriptor)
 872.
      close(228)                              = -1 EBADF (Bad file descriptor)
 873.
      close(227)                              = -1 EBADF (Bad file descriptor)
 874.
      close(226)                              = -1 EBADF (Bad file descriptor)
 875.
      close(225)                              = -1 EBADF (Bad file descriptor)
 876.
      close(224)                              = -1 EBADF (Bad file descriptor)
 877.
      close(223)                              = -1 EBADF (Bad file descriptor)
 878.
      close(222)                              = -1 EBADF (Bad file descriptor)
 879.
      close(221)                              = -1 EBADF (Bad file descriptor)
 880.
      close(220)                              = -1 EBADF (Bad file descriptor)
 881.
      close(219)                              = -1 EBADF (Bad file descriptor)
 882.
      close(218)                              = -1 EBADF (Bad file descriptor)
 883.
      close(217)                              = -1 EBADF (Bad file descriptor)
 884.
      close(216)                              = -1 EBADF (Bad file descriptor)
 885.
      close(215)                              = -1 EBADF (Bad file descriptor)
 886.
      close(214)                              = -1 EBADF (Bad file descriptor)
 887.
      close(213)                              = -1 EBADF (Bad file descriptor)
 888.
      close(212)                              = -1 EBADF (Bad file descriptor)
 889.
      close(211)                              = -1 EBADF (Bad file descriptor)
 890.
      close(210)                              = -1 EBADF (Bad file descriptor)
 891.
      close(209)                              = -1 EBADF (Bad file descriptor)
 892.
      close(208)                              = -1 EBADF (Bad file descriptor)
 893.
      close(207)                              = -1 EBADF (Bad file descriptor)
 894.
      close(206)                              = -1 EBADF (Bad file descriptor)
 895.
      close(205)                              = -1 EBADF (Bad file descriptor)
 896.
      close(204)                              = -1 EBADF (Bad file descriptor)
 897.
      close(203)                              = -1 EBADF (Bad file descriptor)
 898.
      close(202)                              = -1 EBADF (Bad file descriptor)
 899.
      close(201)                              = -1 EBADF (Bad file descriptor)
 900.
      close(200)                              = -1 EBADF (Bad file descriptor)
 901.
      close(199)                              = -1 EBADF (Bad file descriptor)
 902.
      close(198)                              = -1 EBADF (Bad file descriptor)
 903.
      close(197)                              = -1 EBADF (Bad file descriptor)
 904.
      close(196)                              = -1 EBADF (Bad file descriptor)
 905.
      close(195)                              = -1 EBADF (Bad file descriptor)
 906.
      close(194)                              = -1 EBADF (Bad file descriptor)
 907.
      close(193)                              = -1 EBADF (Bad file descriptor)
 908.
      close(192)                              = -1 EBADF (Bad file descriptor)
 909.
      close(191)                              = -1 EBADF (Bad file descriptor)
 910.
      close(190)                              = -1 EBADF (Bad file descriptor)
 911.
      close(189)                              = -1 EBADF (Bad file descriptor)
 912.
      close(188)                              = -1 EBADF (Bad file descriptor)
 913.
      close(187)                              = -1 EBADF (Bad file descriptor)
 914.
      close(186)                              = -1 EBADF (Bad file descriptor)
 915.
      close(185)                              = -1 EBADF (Bad file descriptor)
 916.
      close(184)                              = -1 EBADF (Bad file descriptor)
 917.
      close(183)                              = -1 EBADF (Bad file descriptor)
 918.
      close(182)                              = -1 EBADF (Bad file descriptor)
 919.
      close(181)                              = -1 EBADF (Bad file descriptor)
 920.
      close(180)                              = -1 EBADF (Bad file descriptor)
 921.
      close(179)                              = -1 EBADF (Bad file descriptor)
 922.
      close(178)                              = -1 EBADF (Bad file descriptor)
 923.
      close(177)                              = -1 EBADF (Bad file descriptor)
 924.
      close(176)                              = -1 EBADF (Bad file descriptor)
 925.
      close(175)                              = -1 EBADF (Bad file descriptor)
 926.
      close(174)                              = -1 EBADF (Bad file descriptor)
 927.
      close(173)                              = -1 EBADF (Bad file descriptor)
 928.
      close(172)                              = -1 EBADF (Bad file descriptor)
 929.
      close(171)                              = -1 EBADF (Bad file descriptor)
 930.
      close(170)                              = -1 EBADF (Bad file descriptor)
 931.
      close(169)                              = -1 EBADF (Bad file descriptor)
 932.
      close(168)                              = -1 EBADF (Bad file descriptor)
 933.
      close(167)                              = -1 EBADF (Bad file descriptor)
 934.
      close(166)                              = -1 EBADF (Bad file descriptor)
 935.
      close(165)                              = -1 EBADF (Bad file descriptor)
 936.
      close(164)                              = -1 EBADF (Bad file descriptor)
 937.
      close(163)                              = -1 EBADF (Bad file descriptor)
 938.
      close(162)                              = -1 EBADF (Bad file descriptor)
 939.
      close(161)                              = -1 EBADF (Bad file descriptor)
 940.
      close(160)                              = -1 EBADF (Bad file descriptor)
 941.
      close(159)                              = -1 EBADF (Bad file descriptor)
 942.
      close(158)                              = -1 EBADF (Bad file descriptor)
 943.
      close(157)                              = -1 EBADF (Bad file descriptor)
 944.
      close(156)                              = -1 EBADF (Bad file descriptor)
 945.
      close(155)                              = -1 EBADF (Bad file descriptor)
 946.
      close(154)                              = -1 EBADF (Bad file descriptor)
 947.
      close(153)                              = -1 EBADF (Bad file descriptor)
 948.
      close(152)                              = -1 EBADF (Bad file descriptor)
 949.
      close(151)                              = -1 EBADF (Bad file descriptor)
 950.
      close(150)                              = -1 EBADF (Bad file descriptor)
 951.
      close(149)                              = -1 EBADF (Bad file descriptor)
 952.
      close(148)                              = -1 EBADF (Bad file descriptor)
 953.
      close(147)                              = -1 EBADF (Bad file descriptor)
 954.
      close(146)                              = -1 EBADF (Bad file descriptor)
 955.
      close(145)                              = -1 EBADF (Bad file descriptor)
 956.
      close(144)                              = -1 EBADF (Bad file descriptor)
 957.
      close(143)                              = -1 EBADF (Bad file descriptor)
 958.
      close(142)                              = -1 EBADF (Bad file descriptor)
 959.
      close(141)                              = -1 EBADF (Bad file descriptor)
 960.
      close(140)                              = -1 EBADF (Bad file descriptor)
 961.
      close(139)                              = -1 EBADF (Bad file descriptor)
 962.
      close(138)                              = -1 EBADF (Bad file descriptor)
 963.
      close(137)                              = -1 EBADF (Bad file descriptor)
 964.
      close(136)                              = -1 EBADF (Bad file descriptor)
 965.
      close(135)                              = -1 EBADF (Bad file descriptor)
 966.
      close(134)                              = -1 EBADF (Bad file descriptor)
 967.
      close(133)                              = -1 EBADF (Bad file descriptor)
 968.
      close(132)                              = -1 EBADF (Bad file descriptor)
 969.
      close(131)                              = -1 EBADF (Bad file descriptor)
 970.
      close(130)                              = -1 EBADF (Bad file descriptor)
 971.
      close(129)                              = -1 EBADF (Bad file descriptor)
 972.
      close(128)                              = -1 EBADF (Bad file descriptor)
 973.
      close(127)                              = -1 EBADF (Bad file descriptor)
 974.
      close(126)                              = -1 EBADF (Bad file descriptor)
 975.
      close(125)                              = -1 EBADF (Bad file descriptor)
 976.
      close(124)                              = -1 EBADF (Bad file descriptor)
 977.
      close(123)                              = -1 EBADF (Bad file descriptor)
 978.
      close(122)                              = -1 EBADF (Bad file descriptor)
 979.
      close(121)                              = -1 EBADF (Bad file descriptor)
 980.
      close(120)                              = -1 EBADF (Bad file descriptor)
 981.
      close(119)                              = -1 EBADF (Bad file descriptor)
 982.
      close(118)                              = -1 EBADF (Bad file descriptor)
 983.
      close(117)                              = -1 EBADF (Bad file descriptor)
 984.
      close(116)                              = -1 EBADF (Bad file descriptor)
 985.
      close(115)                              = -1 EBADF (Bad file descriptor)
 986.
      close(114)                              = -1 EBADF (Bad file descriptor)
 987.
      close(113)                              = -1 EBADF (Bad file descriptor)
 988.
      close(112)                              = -1 EBADF (Bad file descriptor)
 989.
      close(111)                              = -1 EBADF (Bad file descriptor)
 990.
      close(110)                              = -1 EBADF (Bad file descriptor)
 991.
      close(109)                              = -1 EBADF (Bad file descriptor)
 992.
      close(108)                              = -1 EBADF (Bad file descriptor)
 993.
      close(107)                              = -1 EBADF (Bad file descriptor)
 994.
      close(106)                              = -1 EBADF (Bad file descriptor)
 995.
      close(105)                              = -1 EBADF (Bad file descriptor)
 996.
      close(104)                              = -1 EBADF (Bad file descriptor)
 997.
      close(103)                              = -1 EBADF (Bad file descriptor)
 998.
      close(102)                              = -1 EBADF (Bad file descriptor)
 999.
      close(101)                              = -1 EBADF (Bad file descriptor)
1000.
      close(100)                              = -1 EBADF (Bad file descriptor)
1001.
      close(99)                               = -1 EBADF (Bad file descriptor)
1002.
      close(98)                               = -1 EBADF (Bad file descriptor)
1003.
      close(97)                               = -1 EBADF (Bad file descriptor)
1004.
      close(96)                               = -1 EBADF (Bad file descriptor)
1005.
      close(95)                               = -1 EBADF (Bad file descriptor)
1006.
      close(94)                               = -1 EBADF (Bad file descriptor)
1007.
      close(93)                               = -1 EBADF (Bad file descriptor)
1008.
      close(92)                               = -1 EBADF (Bad file descriptor)
1009.
      close(91)                               = -1 EBADF (Bad file descriptor)
1010.
      close(90)                               = -1 EBADF (Bad file descriptor)
1011.
      close(89)                               = -1 EBADF (Bad file descriptor)
1012.
      close(88)                               = -1 EBADF (Bad file descriptor)
1013.
      close(87)                               = -1 EBADF (Bad file descriptor)
1014.
      close(86)                               = -1 EBADF (Bad file descriptor)
1015.
      close(85)                               = -1 EBADF (Bad file descriptor)
1016.
      close(84)                               = -1 EBADF (Bad file descriptor)
1017.
      close(83)                               = -1 EBADF (Bad file descriptor)
1018.
      close(82)                               = -1 EBADF (Bad file descriptor)
1019.
      close(81)                               = -1 EBADF (Bad file descriptor)
1020.
      close(80)                               = -1 EBADF (Bad file descriptor)
1021.
      close(79)                               = -1 EBADF (Bad file descriptor)
1022.
      close(78)                               = -1 EBADF (Bad file descriptor)
1023.
      close(77)                               = -1 EBADF (Bad file descriptor)
1024.
      close(76)                               = -1 EBADF (Bad file descriptor)
1025.
      close(75)                               = -1 EBADF (Bad file descriptor)
1026.
      close(74)                               = -1 EBADF (Bad file descriptor)
1027.
      close(73)                               = -1 EBADF (Bad file descriptor)
1028.
      close(72)                               = -1 EBADF (Bad file descriptor)
1029.
      close(71)                               = -1 EBADF (Bad file descriptor)
1030.
      close(70)                               = -1 EBADF (Bad file descriptor)
1031.
      close(69)                               = -1 EBADF (Bad file descriptor)
1032.
      close(68)                               = -1 EBADF (Bad file descriptor)
1033.
      close(67)                               = -1 EBADF (Bad file descriptor)
1034.
      close(66)                               = -1 EBADF (Bad file descriptor)
1035.
      close(65)                               = -1 EBADF (Bad file descriptor)
1036.
      close(64)                               = -1 EBADF (Bad file descriptor)
1037.
      close(63)                               = -1 EBADF (Bad file descriptor)
1038.
      close(62)                               = -1 EBADF (Bad file descriptor)
1039.
      close(61)                               = -1 EBADF (Bad file descriptor)
1040.
      close(60)                               = -1 EBADF (Bad file descriptor)
1041.
      close(59)                               = -1 EBADF (Bad file descriptor)
1042.
      close(58)                               = -1 EBADF (Bad file descriptor)
1043.
      close(57)                               = -1 EBADF (Bad file descriptor)
1044.
      close(56)                               = -1 EBADF (Bad file descriptor)
1045.
      close(55)                               = -1 EBADF (Bad file descriptor)
1046.
      close(54)                               = -1 EBADF (Bad file descriptor)
1047.
      close(53)                               = -1 EBADF (Bad file descriptor)
1048.
      close(52)                               = -1 EBADF (Bad file descriptor)
1049.
      close(51)                               = -1 EBADF (Bad file descriptor)
1050.
      close(50)                               = -1 EBADF (Bad file descriptor)
1051.
      close(49)                               = -1 EBADF (Bad file descriptor)
1052.
      close(48)                               = -1 EBADF (Bad file descriptor)
1053.
      close(47)                               = -1 EBADF (Bad file descriptor)
1054.
      close(46)                               = -1 EBADF (Bad file descriptor)
1055.
      close(45)                               = -1 EBADF (Bad file descriptor)
1056.
      close(44)                               = -1 EBADF (Bad file descriptor)
1057.
      close(43)                               = -1 EBADF (Bad file descriptor)
1058.
      close(42)                               = -1 EBADF (Bad file descriptor)
1059.
      close(41)                               = -1 EBADF (Bad file descriptor)
1060.
      close(40)                               = -1 EBADF (Bad file descriptor)
1061.
      close(39)                               = -1 EBADF (Bad file descriptor)
1062.
      close(38)                               = -1 EBADF (Bad file descriptor)
1063.
      close(37)                               = -1 EBADF (Bad file descriptor)
1064.
      close(36)                               = -1 EBADF (Bad file descriptor)
1065.
      close(35)                               = -1 EBADF (Bad file descriptor)
1066.
      close(34)                               = -1 EBADF (Bad file descriptor)
1067.
      close(33)                               = -1 EBADF (Bad file descriptor)
1068.
      close(32)                               = -1 EBADF (Bad file descriptor)
1069.
      close(31)                               = -1 EBADF (Bad file descriptor)
1070.
      close(30)                               = -1 EBADF (Bad file descriptor)
1071.
      close(29)                               = -1 EBADF (Bad file descriptor)
1072.
      close(28)                               = -1 EBADF (Bad file descriptor)
1073.
      close(27)                               = -1 EBADF (Bad file descriptor)
1074.
      close(26)                               = -1 EBADF (Bad file descriptor)
1075.
      close(25)                               = -1 EBADF (Bad file descriptor)
1076.
      close(24)                               = -1 EBADF (Bad file descriptor)
1077.
      close(23)                               = -1 EBADF (Bad file descriptor)
1078.
      close(22)                               = -1 EBADF (Bad file descriptor)
1079.
      close(21)                               = -1 EBADF (Bad file descriptor)
1080.
      close(20)                               = -1 EBADF (Bad file descriptor)
1081.
      close(19)                               = -1 EBADF (Bad file descriptor)
1082.
      close(18)                               = -1 EBADF (Bad file descriptor)
1083.
      close(17)                               = -1 EBADF (Bad file descriptor)
1084.
      close(16)                               = -1 EBADF (Bad file descriptor)
1085.
      close(15)                               = -1 EBADF (Bad file descriptor)
1086.
      close(14)                               = -1 EBADF (Bad file descriptor)
1087.
      close(13)                               = -1 EBADF (Bad file descriptor)
1088.
      close(12)                               = -1 EBADF (Bad file descriptor)
1089.
      close(11)                               = -1 EBADF (Bad file descriptor)
1090.
      close(10)                               = -1 EBADF (Bad file descriptor)
1091.
      close(9)                                = -1 EBADF (Bad file descriptor)
1092.
      close(8)                                = -1 EBADF (Bad file descriptor)
1093.
      close(7)                                = -1 EBADF (Bad file descriptor)
1094.
      close(6)                                = -1 EBADF (Bad file descriptor)
1095.
      close(5)                                = -1 EBADF (Bad file descriptor)
1096.
      close(4)                                = -1 EBADF (Bad file descriptor)
1097.
      close(3)                                = -1 EBADF (Bad file descriptor)
1098.
      brk(0)                                  = 0x9628000
1099.
      brk(0x9649000)                          = 0x9649000
1100.
      getuid32()                              = 1000
1101.
      getgid32()                              = 1000
1102.
      geteuid32()                             = 1000
1103.
      getegid32()                             = 1000
1104.
      open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
1105.
      open("/usr/share/locale/locale.alias", O_RDONLY) = 3
1106.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
1107.
      mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f5a000
1108.
      read(3, "# Locale name alias data base.\n# "..., 4096) = 2570
1109.
      read(3, ""..., 4096)                    = 0
1110.
      close(3)                                = 0
1111.
      munmap(0xb7f5a000, 4096)                = 0
1112.
      open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
1113.
      open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 3
1114.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=373, ...}) = 0
1115.
      mmap2(NULL, 373, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f5a000
1116.
      close(3)                                = 0
1117.
      open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 3
1118.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0
1119.
      mmap2(NULL, 26048, PROT_READ, MAP_SHARED, 3, 0) = 0xb7f53000
1120.
      close(3)                                = 0
1121.
      open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
1122.
      open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 3
1123.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
1124.
      mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f52000
1125.
      close(3)                                = 0
1126.
      open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
1127.
      open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 3
1128.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
1129.
      mmap2(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f51000
1130.
      close(3)                                = 0
1131.
      open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
1132.
      open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 3
1133.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
1134.
      mmap2(NULL, 155, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f50000
1135.
      close(3)                                = 0
1136.
      open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
1137.
      open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 3
1138.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
1139.
      mmap2(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f4f000
1140.
      close(3)                                = 0
1141.
      open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
1142.
      open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 3
1143.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
1144.
      mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f4e000
1145.
      close(3)                                = 0
1146.
      open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
1147.
      open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 3
1148.
      fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
1149.
      close(3)                                = 0
1150.
      open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3
1151.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0
1152.
      mmap2(NULL, 52, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f4d000
1153.
      close(3)                                = 0
1154.
      open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
1155.
      open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 3
1156.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
1157.
      mmap2(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f4c000
1158.
      close(3)                                = 0
1159.
      open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
1160.
      open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 3
1161.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=962094, ...}) = 0
1162.
      mmap2(NULL, 962094, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7c74000
1163.
      close(3)                                = 0
1164.
      open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
1165.
      open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 3
1166.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
1167.
      mmap2(NULL, 2454, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f4b000
1168.
      close(3)                                = 0
1169.
      open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
1170.
      open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3
1171.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
1172.
      mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f4a000
1173.
      close(3)                                = 0
1174.
      open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
1175.
      open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
1176.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=256316, ...}) = 0
1177.
      mmap2(NULL, 256316, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7c35000
1178.
      close(3)                                = 0
1179.
      rt_sigaction(SIGXFSZ, {SIG_IGN}, {SIG_DFL}, 8) = 0
1180.
      rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
1181.
      access("/home/oren/.nethackrc", F_OK)   = -1 ENOENT (No such file or directory)
1182.
      ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
1183.
      readlink("/proc/self/fd/0", "/dev/pts/10"..., 511) = 11
1184.
      access("/var/run/utmpx", F_OK)          = -1 ENOENT (No such file or directory)
1185.
      open("/var/run/utmp", O_RDWR|O_LARGEFILE|O_CLOEXEC) = -1 EACCES (Permission denied)
1186.
      open("/var/run/utmp", O_RDONLY|O_LARGEFILE|O_CLOEXEC) = 3
1187.
      fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
1188.
      _llseek(3, 0, [0], SEEK_SET)            = 0
1189.
      alarm(0)                                = 0
1190.
      rt_sigaction(SIGALRM, {0xb7e83110, [], 0}, {SIG_DFL}, 8) = 0
1191.
      alarm(1)                                = 0
1192.
      fcntl64(3, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}) = 0
1193.
      read(3, "\2\0\0\0\0\0\0\0~\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1194.
      read(3, "\1\0\0\0002\0\0\0~\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1195.
      read(3, "\6\0\0\0\177\10\0\0tty2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1196.
      read(3, "\6\0\0\0{\10\0\0tty4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1197.
      read(3, "\6\0\0\0|\10\0\0tty5\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1198.
      read(3, "\6\0\0\0\202\10\0\0tty3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1199.
      read(3, "\6\0\0\0\203\10\0\0tty6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1200.
      read(3, "\7\0\0\0\366\v\0\0tty1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1201.
      read(3, "\7\0\0\0k\r\0\0pts/0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1202.
      read(3, "\10\0\0\0\355\r\0\0pts/2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1203.
      read(3, "\7\0\0\0\371\r\0\0pts/3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1204.
      read(3, "\7\0\0\0\220T\0\0pts/4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1205.
      read(3, "\7\0\0\0h\27\0\0pts/5\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1206.
      read(3, "\7\0\0\0)\31\0\0pts/6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1207.
      read(3, "\10\0\0\0\1i\0\0pts/7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1208.
      read(3, "\10\0\0\0%i\0\0pts/8\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1209.
      read(3, "\10\0\0\0\247\30\0\0pts/8\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1210.
      read(3, "\10\0\0\0l\4\0\0pts/8\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1211.
      read(3, "\10\0\0\0\0q\0\0pts/9\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1212.
      read(3, "\10\0\0\0\267\22\0\0pts/10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1213.
      read(3, "\10\0\0\0-\36\0\0pts/11\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1214.
      read(3, "\10\0\0\0\311\3\0\0pts/12\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1215.
      read(3, "\7\0\0\0_\23\0\0pts/10\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
1216.
      fcntl64(3, F_SETLKW, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
1217.
      alarm(0)                                = 1
1218.
      rt_sigaction(SIGALRM, {SIG_DFL}, NULL, 8) = 0
1219.
      close(3)                                = 0
1220.
      socket(PF_FILE, 0x80801 /* SOCK_??? */, 0) = 3
1221.
      connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"...}, 110) = -1 ENOENT (No such file or directory)
1222.
      close(3)                                = 0
1223.
      socket(PF_FILE, 0x80801 /* SOCK_??? */, 0) = 3
1224.
      connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"...}, 110) = -1 ENOENT (No such file or directory)
1225.
      close(3)                                = 0
1226.
      open("/etc/nsswitch.conf", O_RDONLY)    = 3
1227.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
1228.
      mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c34000
1229.
      read(3, "# /etc/nsswitch.conf\n#\n# Example "..., 4096) = 513
1230.
      read(3, ""..., 4096)                    = 0
1231.
      close(3)                                = 0
1232.
      munmap(0xb7c34000, 4096)                = 0
1233.
      open("/etc/ld.so.cache", O_RDONLY)      = 3
1234.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=70733, ...}) = 0
1235.
      mmap2(NULL, 70733, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7c23000
1236.
      close(3)                                = 0
1237.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
1238.
      open("/lib/tls/i686/cmov/libnss_compat.so.2", O_RDONLY) = 3
1239.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\16\0\0004\0\0\0\204"..., 512) = 512
1240.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=30436, ...}) = 0
1241.
      mmap2(NULL, 33356, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c1a000
1242.
      mmap2(0xb7c21000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xb7c21000
1243.
      close(3)                                = 0
1244.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
1245.
      open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
1246.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p1\0\0004\0\0\0\234"..., 512) = 512
1247.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=87804, ...}) = 0
1248.
      mmap2(NULL, 100328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c01000
1249.
      mmap2(0xb7c16000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xb7c16000
1250.
      mmap2(0xb7c18000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7c18000
1251.
      close(3)                                = 0
1252.
      mprotect(0xb7c16000, 4096, PROT_READ)   = 0
1253.
      mprotect(0xb7c21000, 4096, PROT_READ)   = 0
1254.
      munmap(0xb7c23000, 70733)               = 0
1255.
      open("/etc/ld.so.cache", O_RDONLY)      = 3
1256.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=70733, ...}) = 0
1257.
      mmap2(NULL, 70733, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7c23000
1258.
      close(3)                                = 0
1259.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
1260.
      open("/lib/tls/i686/cmov/libnss_nis.so.2", O_RDONLY) = 3
1261.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\31\0\0004\0\0\0\314"..., 512) = 512
1262.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=38444, ...}) = 0
1263.
      mmap2(NULL, 41532, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bf6000
1264.
      mmap2(0xb7bff000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb7bff000
1265.
      close(3)                                = 0
1266.
      access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
1267.
      open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 3
1268.
      read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0\0004\0\0\0\250"..., 512) = 512
1269.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=42504, ...}) = 0
1270.
      mmap2(NULL, 45720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bea000
1271.
      mmap2(0xb7bf4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xb7bf4000
1272.
      close(3)                                = 0
1273.
      mprotect(0xb7bf4000, 4096, PROT_READ)   = 0
1274.
      mprotect(0xb7bff000, 4096, PROT_READ)   = 0
1275.
      munmap(0xb7c23000, 70733)               = 0
1276.
      open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
1277.
      fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
1278.
      _llseek(3, 0, [0], SEEK_CUR)            = 0
1279.
      fstat64(3, {st_mode=S_IFREG|0644, st_size=1684, ...}) = 0
1280.
      mmap2(NULL, 1684, PROT_READ, MAP_SHARED, 3, 0) = 0xb7f49000
1281.
      _llseek(3, 1684, [1684], SEEK_SET)      = 0
1282.
      munmap(0xb7f49000, 1684)                = 0
1283.
      close(3)                                = 0
1284.
      open("/etc/shadow", O_RDONLY|O_CLOEXEC) = -1 EACCES (Permission denied)
1285.
      ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
1286.
      readlink("/proc/self/fd/0", "/dev/pts/10"..., 4095) = 11
1287.
      stat64("/dev/pts/10", {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 10), ...}) = 0
1288.
      geteuid32()                             = 1000
1289.
      getegid32()                             = 1000
1290.
      open("/dev/pts/10", O_RDWR|O_NONBLOCK)  = 3
1291.
      geteuid32()                             = 1000
1292.
      getegid32()                             = 1000
1293.
      close(3)                                = 0
1294.
      ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
1295.
      umask(0)                                = 022
1296.
      stat64("/var/run/screen", {st_mode=S_IFDIR|0755, st_size=100, ...}) = 0
1297.
      fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 10), ...}) = 0
1298.
      mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f49000
1299.
      write(1, "Directory '/var/run/screen' must "..., 49) = 49
1300.
      exit_group(1)
```

I seet 2 interesting lines there: 
open("/etc/shadow", O_RDONLY|O_CLOEXEC) = -1 EACCES (Permission denied) 
open("/var/run/utmp", O_RDWR|O_LARGEFILE|O_CLOEXEC) = -1 EACCES (Permission denied)

here are my shadow file and the one guest is using:
-rw------- 1 root root 124 2009-06-03 17:28 /home/jail/guest/etc/shadow

-rw-r----- 1 root shadow 1196 2009-06-03 17:28 /etc/shadow

edit:
TheSheep from #xubuntu gave me his advice: 
"screen goes too deeply into various system internals and it doesn't chroot well. you would probably run into further issues after solving that.
why not give him a separate account and chgrp/chown the file so that you can both edit it?"

unfortunately I don't understand what he means by separate account.

Any insight/suggestions would be great!

---

### Post by orengolan on 2009-07-16
here is the final result:
[http://orengolan.blogspot.com/2009/06/remote-pair-programming-using-ssh.html](http://orengolan.blogspot.com/2009/06/remote-pair-programming-using-ssh.html)

---

