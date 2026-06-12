---
title: "How to open files with grub_open_file"
date: 2009-03-19
forum: General Help
---

### Post by garymeerschaert on 2009-03-19
I need to modify grub for a project in my security class. I am adding a a check of a key stored on a usb drive. I also have the key stored in the /boot/grub2, /boot/grub, and /boot. I can not open any of them. My system dual-boots, and the fedora install is in hd0,1.

My code is shown (extra tracing statements included)

static void
grub_key_check (void)
{

  grub_file_t      key_disk_file;
  grub_file_t      key_usb_file;  

  char             usb_key[512];
  char             disk_key[512];

  char             key_match;

  int              i;
  const char *prefix;

  prefix = grub_env_get ("prefix");
grub_printf("In key check\n");
  key_match = 'f';

  /* look for a key file on the disk */
grub_printf("before disk file open\n");
  key_disk_file = grub_file_open("(hd0)grub/key");
grub_printf("after disk file open\n");
  if ( ! key_disk_file )
    {
      grub_printf("No disk key file\n");
grub_printf("before return\n");
      return;
    }
  
grub_printf("After disk file open\n");
  /* read in the key from the key file. Must be 512 char*/
  if ( grub_file_read(key_disk_file, disk_key,512) != 512)
    {
      grub_printf("Disk key file wrong size\n");
      sleep(30);
      return;
    }

grub_printf("After disk file read\n");
  /* read the key file from the usb drive & compare */
  while (key_match == 'f')
    {

grub_printf("top of key match loop\n");
      while ( (key_usb_file = grub_file_open("(hd0)key")) == (grub_file_t)0)
        {
grub_printf("usb file open failed\n");
          grub_printf("Insert key\n");
          sleep(30);
        }  

grub_printf("usb file open worked\n");
      if (grub_file_read (key_usb_file, usb_key, 512) != 512)
        {
grub_printf("usb file read failed\n");
          grub_file_close(key_usb_file);
          grub_printf("Insert key\n");
          sleep(30);
          continue;
        }
grub_printf("usb file read worked\n");

grub_printf("before key check\n");
grub_printf("usb file read worked\n");

grub_printf("before key check\n");
      for (i=0; i<512; i++)
        {
          if (disk_key[i] != usb_key[i])
            {
grub_printf("Key match failed at %d\n",i);
               break;
            } 
        }
grub_printf("Key check passed\n");
      if (i == 512) key_match = 't';
    }
grub_printf("Bottom of key_check\n");
}

/* The main routine.  */
void
grub_main (void)
{
  /* First of all, initialize the machine.  */
  grub_machine_init ();
  /* First of all, initialize the machine.  */
  grub_machine_init ();
grub_printf("hello - before key_check\n");
  /* check for USB drive key */
  grub_key_check();
grub_printf("After key check\n");
  /* Hello.  */
  grub_setcolorstate (GRUB_TERM_COLOR_HIGHLIGHT);
  grub_printf ("Welcome to GRUB!\n\n");
  grub_setcolorstate (GRUB_TERM_COLOR_STANDARD);


There are some trace satements in the file.c routine also (not shown). 

The output I get is:
./grub-emu -r /boot
hello - before key_check
In key check
before disk file open
in grub_file_open, file = (hd0)grub/key
In grub_file_get_device_name, file = (hd0)grub/key
Malloc return = 0
Device name = hd0
device name = hd0
file name now = grub/key
After device_open
after disk file open
No disk key file
before return
After key check
Welcome to GRUB!

Segmentation fault

I have tried the file name as (hd0)/boot/key, (hd0)/boot/grub/key with the same results.

Can anyone tell me what I am doing wrong?

Thanks,
    Gary

---

### Post by bapoumba on 2009-03-20
It is our policy on UF not to allow homework questions. Closing the thread, sorry.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

