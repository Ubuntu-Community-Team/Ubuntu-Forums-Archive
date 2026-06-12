---
title: "How to get rid of ANY graphics till login"
date: 2011-09-22
forum: Desktop Environments
---

### Post by agroszer on 2011-09-22
Using 11.04. How to get rid of ANY graphics/mode switches until the login appears?
I want that old behavour when everything was just text.
My problem is that there seems to be some invisible question/missing fstab drive.

---

### Post by Elfy on 2011-09-22
> My problem is that there seems to be some invisible question/missing fstab drive.IF that's the case try running 

```
sudo mount -a 
```

Otherwise remove the quiet splash lines from /etc/default/grub

```
gksudo gedit /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_CMDLINE_LINUX_DEFAULT=""

run ```
sudo update-grub
```

---

### Post by agroszer on 2011-09-23
Removing quiet splash didn't do it.

After

```

GRUB_TERMINAL=console

```

```

sudo apt-get install plymouth-theme-text

```

```

sudo mv /etc/init/plymouth-splash.conf /etc/init/plymouth-splash.conf.disabled

```

It's a bit better, now I can see fsck and the services starting.

But there are STILL mode switches.

FTR, my /etc/default/grub:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="acpi_enforce_resources=lax"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by garvinrick4 on 2011-09-23
If there is a theme for it then you can run and choose the text theme like any other theme
I would imagine.
```
sudo update-alternatives --config default.plymouth 
```Choose your text theme by number install it and run:
```
sudo update-initramfs -u
```I have never used text theme nor installed it but if it is a theme no reason it will
not install like any other plymouth theme.

---

### Post by agroszer on 2011-09-26
Had to run

```

sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth 100

```

to get a selection with
```

sudo update-alternatives --config default.plymouth

```

plymouth-theme-ubuntu-text was already installed!

---

### Post by garvinrick4 on 2011-09-26
Do not forget to update-initramfs. Makes all the sense in the world that you have to install themes before you can configure theme. Enjoy reading your text. Have a good evening

---

### Post by agroszer on 2011-09-26
I guessed installing the package should be enough... let's try rebooting ;)

---

