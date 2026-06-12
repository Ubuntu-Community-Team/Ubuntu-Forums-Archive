---
title: "Boot to windows button"
date: 2007-10-08
forum: Desktop Environments
---

### Post by mari0 on 2007-10-08
Hi

I have a dual boot system (windows xp, ubuntu) installed on my PC.
I'd like to know if there is any way i could add a "Boot to windows" button to the shutdown menu in ubuntu so i can just click this and my PC restarts and automatically starts Windows.

Something like this would also be cool for windows (but i guess this will be a lot harder to do there) :D

so, if anyone knows something like this, let me know ;)

---

### Post by Ant1jr on 2007-10-08
Technically it should be possible if you modify GRUB, but it won't be easy.

---

### Post by mari0 on 2007-10-11
hmm i guess i'll just keep it the way it is then

thx

---

### Post by explemonk on 2007-10-12
openSUSE does this (auto-boot to any select of your grub menu), but I don't know how exactly it's implemented.  I agree it is a nice feature to have.

---

### Post by nchase on 2007-10-12
This is a feature I'd like to see too. Anyone know more about this?

---

### Post by lisati on 2007-10-12
> **explemonk said:**
> openSUSE does this (auto-boot to any select of your grub menu), but I don't know how exactly it's implemented.  I agree it is a nice feature to have.

Just a thought: have the shut-down process modify menu.lst in some way, or add a "run at startup" or "run once" feature to grub, similar to Windows......

---

### Post by eurgain on 2007-10-12
> **mari0 said:**
> Hi

I have a dual boot system (windows xp, ubuntu) installed on my PC.
I'd like to know if there is any way i could add a "Boot to windows" button to the shutdown menu in ubuntu so i can just click this and my PC restarts and automatically starts Windows.

Something like this would also be cool for windows (but i guess this will be a lot harder to do there) :D

so, if anyone knows something like this, let me know ;)

AFAK, SUSE does this by scripting the command **grubonce**, which is a bit like **lilo -R**, in that it allows you to specify which one of several boot options should be *automatically* selected at the next boot and suppress the boot menu.

However, grubonce seems to be a SUSE-only thing (or, at least, a non-Ubuntu thing) so you might have to get the source and implement grubonce yourself.  I don't think it works by modifying menu.lst.  FWIW, the perl source of /usr/sbin/grubonce from my SUSE 10.2 box is reproduced below.

If you get nowhere with grubonce, you could use lilo instead of grub as your bootloader, because the ability to specify the next OS to load using a command is built in.  lilo works fine, but you have to take care to update the boot code (just a quick, single command-line operation) whenever you update the kernel.

HTH
A

fuchsia:/home/eurgain # which grubonce
/usr/sbin/grubonce
fuchsia:/home/eurgain # exit
eurgain@fuchsia:~> cat /usr/sbin/grubonce 
#!/usr/bin/perl

# Keep this sort of configurable for the future.
$GRUBDIR="/boot/grub";

# Parse the menu file, and see if we can get a match for a maybe given arg.
open(MENU, "<$GRUBDIR/menu.lst") || die "no menu.lst in $GRUBDIR";
$gotit = 0;
$titleno = -1;
$global_default = undef;
while(<MENU>) {
  m,\s*default\s+(.+), && $titleno == -1 && ($global_default = $1);
  next unless m,\s*title\s+(.*),i;
  $title_name = $1;
  $titleno++;

  if (@ARGV > 0) {
    # Argument may be entirely numerical, in which case it is an index,
    # or a perl RE that leads to the first title matching.
    if (( $ARGV[0] =~ m,[0-9]+, && $titleno    eq   $ARGV[0] ) ||
        ( $ARGV[0] !~ m,[0-9]+, && $title_name =~ m,$ARGV[0],i) ) {
      $gotit = 1;
      last;
    }
  } else {
    print "$titleno: $title_name\n";
  }
}
close(MENU);

print "Warning: you haven't set a global default!\n" if !defined($global_default);

# Without a command line argument, we have now listet the titles and are done.
exit 0 if @ARGV < 1;

# Else the user wants to write the default file. We have better found a match!
if ($gotit > 0) {
  print "Warning: your global default is 'saved'; changing default permanently!"
    if $global_default eq "saved";

  print "Using entry #$titleno: $title_name\n";

  # set the magic one-time flag
  $titleno |= 0x4000;

  open(DEFFILE, ">$GRUBDIR/default") ||
    die "Cannot open default file for writing";
  $buf = $titleno . "\0" .  "\n" x 9;
  syswrite(DEFFILE, $buf, 10);
  close(DEFFILE);

  exit 0;
} else {
  print $ARGV[0] . " not found in $GRUBDIR/menu.lst\n";
  exit 1;
}

eurgain@fuchsia:~>

---

### Post by lordadi on 2008-06-19
Hi,

There is a simple GRUB way to do it, although I have not been able to make it work on Ubuntu (Help, anyone?). Here it is:[http://www.pcworld.com/article/id,118200/article.html]("http://www.pcworld.com/article/id,118200/article.html") (It is also for lilo, just follow the instructions).


If anyone gets this working please let me know how you did it.

Cheers,

Lordadi.

---

