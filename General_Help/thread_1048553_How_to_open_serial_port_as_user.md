---
title: "How to open serial port as user"
date: 2009-01-23
forum: General Help
---

### Post by lu333031 on 2009-01-23
Hi,

Running ubuntu 7.10 on a 32-bit machine.

I (ordinary user on linux machine) am unable to open a serial port when I run a program compiled and owned by superuser. 

The test file lutest.c is given below. The actions performed and the behavior seen is described at the top of the file.  Please help me run this assuming that I will not have access to superuser password to do any "sudo" type operations. 

When run on ubuntu as a regular user, the program prints the error message in main(), when run as a super user, it opens and closes the port successfully. It apparently doesn't do so on other linux flavors (I had posted my problem on linuxforums) and enables a non-root user to open the port.

How can I open a port as a user on ubuntu? 

(In the code below, suser is the super user with system privileges and ownership of lutest. and user is an ordinary user account created with "sudo adduser...." command by suser)


Thanks you.

lu

--------------------------------------------------------------

/*
 * File: lutest.c
 *
 *  executed as follows:
 *    (log in as suser in a shell)
 *    suser$ gcc -o lutest lutest.c
 *    suser$ chmod 4755 lutest
 *    suser$ lutest
 *    Closing port
 *    suser$
 *
 *
 *  executed again as follows:
 *    (log in as user in another shell)
 *    user$ ~suser/lutest
 *    Error 13 in open()
 *    user$
 */

#include <errno.h>
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>


static uid_t euid, ruid;

/* Restore the effective UID to its original value. */

static void do_setuid (void)
{
    int status;

    #ifdef _POSIX_SAVED_IDS
           status = seteuid (euid);
    #else
           status = setreuid (ruid, euid);
    #endif

    if (status < 0)
    {
           fprintf (stderr, "Couldn't set uid.\n");
           exit (status);
    }
}


/* Set the effective UID to the real UID. */

static void undo_setuid (void)
{
   int status;

   #ifdef _POSIX_SAVED_IDS
           status = seteuid (ruid);
   #else
           status = setreuid (euid, ruid);
   #endif

   if (status < 0)
   {
           fprintf (stderr, "Couldn't set uid.\n");
           exit (status);
   }
}


int main()
{
   ruid = getuid ();
   euid = geteuid ();

   do_setuid();

   int fd = open("/dev/ttyS0", (O_RDWR | O_NOCTTY | O_NONBLOCK));
   if (fd == -1)
   {
          printf("Error %d in open()\n", errno);
   }
   else
   {
          printf("Closing port\n");
          close(fd);
   }

   undo_setuid ();
}

---

### Post by lu333031 on 2009-01-29
Learned from elsewhere - adding user to the dialout group solves the problem:

sudo adduser <username> dialout

No need for modifying uid etc.

---

