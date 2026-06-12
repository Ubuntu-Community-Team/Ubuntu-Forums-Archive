---
title: "fsck died with exit status 4"
date: 2009-02-22
forum: General Help
---

### Post by libihero on 2009-02-22
My computer froze, so I shut it down by holding on to the power button, and when it restarts, it goes through a process then ends with this:

-An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root file system mounted in read-only mode.
-The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started. After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this hell
root@ednan-laptop:~#

what do i type in, or do in general?
thanks!

---

### Post by taurus on 2009-02-22
```
fsck /dev/sda1
```
If /dev/sda1 is the one that fails to fsck during the booting process.

---

### Post by libihero on 2009-02-22
it is now asking if i should ignore error reading block 1245187
do i ignore?

---

### Post by taurus on 2009-02-22
Yes.

---

### Post by libihero on 2009-02-22
now it's asking if i should force rewrite... do i say yes to that too??  is that gonna reformat my computer?
thanks for all ur help

---

### Post by taurus on 2009-02-22
Fsck doesn't reformat your harddrive.

```

FSCK(8)                                                                FSCK(8)

NAME
       fsck - check and repair a Linux file system

SYNOPSIS
       fsck  [  -sAVRTMNP  ] [ -C [ fd ] ] [ -t fstype ] [filesys ... ] [--] [
       fs-specific-options ]

DESCRIPTION
       fsck is used to check and optionally repair one or more Linux file sys&#8208;
       tems.   filesys  can  be  a device name (e.g.  /dev/hdc1, /dev/sdb2), a
       mount point (e.g.  /, /usr, /home), or an ext2 label or UUID  specifier
       (e.g.   UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd or LABEL=root).  Nor&#8208;
       mally, the fsck program will try to  handle  filesystems  on  different
       physical  disk  drives  in  parallel to reduce the total amount of time
       needed to check all of the filesystems.

       If no filesystems are specified on the command line, and the -A  option
       is  not  specified,  fsck  will  default  to  checking  filesystems  in
       /etc/fstab serially.  This is equivalent to the -As options.

       The exit code returned by fsck is the sum of the following conditions:
            0    - No errors
            1    - File system errors corrected
            2    - System should be rebooted
            4    - File system errors left uncorrected
            8    - Operational error
            16   - Usage or syntax error
            32   - Fsck canceled by user request
            128  - Shared library error
       The exit code returned when multiple file systems are  checked  is  the
       bit-wise OR of the exit codes for each file system that is checked.

       In  actuality,  fsck  is simply a front-end for the various file system
       checkers (fsck.fstype) available under Linux.  The file system-specific
       checker  is  searched for in /sbin first, then in /etc/fs and /etc, and
       finally in the directories listed in  the  PATH  environment  variable.
       Please  see  the  file system-specific checker manual pages for further
       details.

OPTIONS
       -s     Serialize fsck operations.  This is  a  good  idea  if  you  are
              checking  multiple filesystems and the checkers are in an inter&#8208;
              active mode.  (Note: e2fsck(8) runs in an  interactive  mode  by
              default.   To  make e2fsck(8) run in a non-interactive mode, you             
              must either specify the -p or -a option, if you wish for  errors
              to  be corrected automatically, or the -n option if you do not.)

       -t fslist
              Specifies the type(s) of file system to be checked.  When the -A
              flag  is  specified,  only  filesystems  that  match  fslist are
              checked.  The fslist parameter  is  a  comma-separated  list  of
              filesystems  and  options specifiers.  All of the filesystems in
              this comma-separated list may be prefixed by a negation operator
              &#8217;no&#8217;  or  &#8217;!&#8217;,  which  requests  that only those filesystems not
              listed in fslist will be checked.  If all of the filesystems  in
              fslist  are not prefixed by a negation operator, then only those
              filesystems listed in fslist will be checked.

              Options  specifiers  may  be  included  in  the  comma-separated
              fslist.   They  must  have  the  format  opts=fs-option.   If an
              options specifier is present, then only filesystems  which  con&#8208;
              tain  fs-option  in their mount options field of /etc/fstab will
              be checked.  If the options specifier is prefixed by a  negation
              operator, then only those filesystems that do not have fs-option
              in their mount options field of /etc/fstab will be checked.

              For example, if opts=ro appears in fslist, then only filesystems
              listed in /etc/fstab with the ro option will be checked.

              For compatibility with Mandrake distributions whose boot scripts
              depend upon an unauthorized UI change to the fsck program, if  a
              filesystem  type of loop is found in fslist, it is treated as if
              opts=loop were specified as an argument to the -t option.

              Normally, the  filesystem  type  is  deduced  by  searching  for
              filesys  in  the  /etc/fstab  file  and  using the corresponding
              entry.  If the type can not be deduced, and there is only a sin&#8208;
              gle  filesystem given as an argument to the -t option, fsck will
              use the specified filesystem type.  If this type is  not  avail&#8208;
              able,  then  the  default  file  system type (currently ext2) is
              used.

       -A     Walk through the /etc/fstab file and try to check all file  sys&#8208;
              tems in one run.  This option is typically used from the /etc/rc
              system initialization file, instead  of  multiple  commands  for
              checking a single file system.

              The  root  filesystem will be checked first unless the -P option
              is specified (see  below).   After  that,  filesystems  will  be
              checked  in  the  order  specified  by the fs_passno (the sixth)
              field in the /etc/fstab  file.   Filesystems  with  a  fs_passno
              value  of 0 are skipped and are not checked at all.  Filesystems
              with a fs_passno value of greater than zero will be  checked  in
              order,  with  filesystems with the lowest fs_passno number being
              checked first.  If there are multiple filesystems with the  same
              pass  number,  fsck  will  attempt  to  check  them in parallel,
              although it will avoid running multiple filesystem checks on the
              same physical disk.

              Hence, a very common configuration in /etc/fstab files is to set
              the root filesystem to have a fs_passno value of 1  and  to  set
              all other filesystems to have a fs_passno value of 2.  This will
              allow fsck to automatically run filesystem checkers in  parallel
              if  it  is  advantageous  to do so.  System administrators might
              choose not to use this configuration if they need to avoid  mul&#8208;
              tiple  filesystem checks running in parallel for some reason ---
              for example, if the machine in question is short  on  memory  so
              that excessive paging is a concern.

       -C [  fd  ]
              Display  completion/progress  bars for those filesystem checkers
              (currently only for ext2 and ext3) which  support  them.    Fsck
              will  manage  the  filesystem  checkers so that only one of them
              will display a progress bar at a time.  GUI front-ends may spec&#8208;
              ify  a file descriptor fd, in which case the progress bar infor&#8208;
              mation will be sent to that file descriptor.

       -M     Do not check mounted filesystems and return an exit  code  of  0
              for mounted filesystems.

       -N     Don&#8217;t execute, just show what would be done.

       -P     When  the  -A flag is set, check the root filesystem in parallel
              with the other filesystems.  This is not the safest thing in the
              world  to  do,  since  if the root filesystem is in doubt things
              like the e2fsck(8) executable might be corrupted!   This  option
              is  mainly provided for those sysadmins who don&#8217;t want to repar&#8208;
              tition the root filesystem to be small  and  compact  (which  is
              really the right solution).

       -R     When  checking  all file systems with the -A flag, skip the root
              file system (in case it&#8217;s already mounted read-write).

       -T     Don&#8217;t show the title on startup.

       -V     Produce verbose output, including all file system-specific  com&#8208;
              mands that are executed.

       fs-specific-options
              Options  which  are  not  understood  by  fsck are passed to the
              filesystem-specific checker.   These  arguments  must  not  take
              arguments,  as  there  is no way for fsck to be able to properly
              guess which arguments take options and which don&#8217;t.

              Options and arguments which follow the -- are  treated  as  file
              system-specific options to be passed to the file system-specific
              checker.

              Please note that fsck is not designed to pass  arbitrarily  com&#8208;
              plicated  options  to  filesystem-specific  checkers.  If you&#8217;re
              doing something complicated, please just execute the filesystem-
              specific  checker directly.  If you pass fsck some horribly com&#8208;
              plicated option and  arguments,  and  it  doesn&#8217;t  do  what  you
              expect,  don&#8217;t bother reporting it as a bug.  You&#8217;re almost cer&#8208;
              tainly doing something that you shouldn&#8217;t be doing with fsck.

       Options to different filesystem-specific fsck&#8217;s are  not  standardized.
       If  in  doubt,  please consult the man pages of the filesystem-specific
       checker.  Although not guaranteed, the following options are  supported
       by most file system checkers:

       -a     Automatically  repair the file system without any questions (use
              this option with caution).  Note that e2fsck(8) supports -a  for
              backwards compatibility only.  This option is mapped to e2fsck&#8217;s
              -p option which is safe to use, unlike the -a option  that  some
              file system checkers support.

       -n     For  some filesystem-specific checkers, the -n option will cause
              the fs-specific fsck to avoid attempting to repair any problems,
              but  simply report such problems to stdout.  This is however not
              true  for  all  filesystem-specific  checkers.   In  particular,
              fsck.reiserfs(8)  will  not  report any corruption if given this
              option.  fsck.minix(8) does not support the -n option at all.

       -r     Interactively repair the  filesystem  (ask  for  confirmations).
              Note:  It is generally a bad idea to use this option if multiple
              fsck&#8217;s are being run  in  parallel.   Also  note  that  this  is
              e2fsck&#8217;s default behavior; it supports this option for backwards
              compatibility reasons only.

       -y     For some filesystem-specific checkers, the -y option will  cause
              the  fs-specific  fsck  to  always  attempt  to fix any detected
              filesystem corruption automatically.  Sometimes an expert may be
              able  to do better driving the fsck manually.  Note that not all
              filesystem-specific checkers implement this option.  In particu&#8208;
              lar  fsck.minix(8)  and  fsck.cramfs(8)  does not support the -y
              option as of this writing.

AUTHOR
       Theodore Ts&#8217;o (tytso@mit.edu)

FILES
       /etc/fstab.

ENVIRONMENT VARIABLES
       The fsck program&#8217;s behavior is affected by  the  following  environment
       variables:

       FSCK_FORCE_ALL_PARALLEL
              If  this  environment  variable is set, fsck will attempt to run
              all of the specified  filesystems  in  parallel,  regardless  of
              whether  the filesystems appear to be on the same device.  (This
              is useful for RAID systems or high-end storage systems  such  as
              those sold by companies such as IBM or EMC.)

       FSCK_MAX_INST
              This  environment variable will limit the maximum number of file
              system checkers that can be running at one  time.   This  allows
              configurations  which have a large number of disks to avoid fsck
              starting too many file system  checkers  at  once,  which  might
              overload  CPU  and memory resources available on the system.  If
              this value is zero, then an unlimited number of processes can be
              spawned.   This is currently the default, but future versions of
              fsck may attempt to automatically determine how many file system
              checks  can  be  run based on gathering accounting data from the
              operating system.

       PATH   The PATH environment variable is used to find file system check&#8208;
              ers.   A  set  of  system directories are searched first: /sbin,
              /sbin/fs.d, /sbin/fs, /etc/fs, and /etc.  Then the set of direc&#8208;
              tories found in the PATH environment are searched.

       FSTAB_FILE
              This  environment  variable  allows  the system administrator to
              override the standard location of the /etc/fstab  file.   It  is
              also useful for developers who are testing fsck.

SEE ALSO
       fstab(5),  mkfs(8),  fsck.ext2(8)  or fsck.ext3(8) or e2fsck(8), cramf&#8208;
       sck(8),   fsck.minix(8),   fsck.msdos(8),   fsck.jfs(8),   fsck.nfs(8),
       fsck.vfat(8), fsck.xfs(8), fsck.xiafs(8), reiserfsck(8).

E2fsprogs version 1.41.3         October 2008                          FSCK(8)

```

---

