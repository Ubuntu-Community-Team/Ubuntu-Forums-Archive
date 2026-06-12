---
title: "Conky 1.7.2 from Ubuntu 8.04 problem .."
date: 2009-10-08
forum: Desktop Environments
---

### Post by Kaizzer on 2009-10-08
Ok here is the deal .. 
1) downloaded the conky-1.7.2.tar.bz2 file and decompresed in ~/.../.../Desktop/Installers/Conky/.. folder
2) installed X11 package .. and Lua51 .. 
3) ./configure raises a "conky 1.7.2 configured successfully:"
4) sudo make install rises tons of errors.. 

```

jelopez@jelopez-laptop:~/Desktop/Instaladores/Conky/conky-1.7.2$ sudo make install
Making install in src
make[1]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/src'
make  install-am
make[2]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/src'
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-conky.o -MD -MP -MF .deps/conky-conky.Tpo -c -o conky-conky.o `test -f 'conky.c' || echo './'`conky.c
mv -f .deps/conky-conky.Tpo .deps/conky-conky.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\" -DPACKAGE_LIBDIR=\"/usr/local/lib/conky\"   -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -MT conky-llua.o -MD -MP -MF .deps/conky-llua.Tpo -c -o conky-llua.o `test -f 'llua.c' || echo './'`llua.c
mv -f .deps/conky-llua.Tpo .deps/conky-llua.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -lpthread -lm  -o conky  conky-conf_cookie.o   conky-colours.o conky-common.o conky-conky.o  conky-fs.o conky-hddtemp.o conky-apcupsd.o conky-linux.o conky-top.o conky-diskio.o conky-users.o conky-sony.o  conky-mail.o conky-mixer.o conky-mpd.o conky-libmpdclient.o conky-moc.o  conky-libtcp-portmon.o conky-tcp-portmon.o    conky-llua.o conky-timed_thread.o conky-mboxscan.o conky-x11.o conky-fonts.o   conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-algebra.o    -lm -lX11    -llua5.1    -lXext   -lXdamage -lXfixes   -lXft -lfontconfig   -lglib-2.0   -lrt
../libtool: line 827: X--tag=CC: command not found
../libtool: line 860: libtool: ignoring unknown tag : command not found
../libtool: line 827: X--mode=link: command not found
../libtool: line 994: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 995: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 2239: X-I/usr/include/lua5.1: No such file or directory
../libtool: line 2239: X-I/usr/include/freetype2: No such file or directory
../libtool: line 2239: X-I/usr/include/glib-2.0: No such file or directory
../libtool: line 2239: X-I/usr/lib/glib-2.0/include: No such file or directory
../libtool: line 2239: X-Wall: command not found
../libtool: line 2239: X-W: command not found
../libtool: line 2408: Xconky: command not found

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

../libtool: line 2420: Xconky: command not found
../libtool: line 2558: X-lpthread: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lX11: command not found
../libtool: line 2558: X-llua5.1: command not found
../libtool: line 2558: X-lXext: command not found
../libtool: line 2558: X-lXdamage: command not found
../libtool: line 2558: X-lXfixes: command not found
../libtool: line 2558: X-lXft: command not found
../libtool: line 2558: X-lfontconfig: command not found
../libtool: line 2558: X-lglib-2.0: command not found
../libtool: line 2558: X-lrt: command not found
../libtool: line 2558: X-lpthread: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lX11: command not found
../libtool: line 2558: X-llua5.1: command not found
../libtool: line 2558: X-lXext: command not found
../libtool: line 2558: X-lXdamage: command not found
../libtool: line 2558: X-lXfixes: command not found
../libtool: line 2558: X-lXft: command not found
../libtool: line 2558: X-lfontconfig: command not found
../libtool: line 2558: X-lglib-2.0: command not found
../libtool: line 2558: X-lrt: command not found
../libtool: line 2558: X-lpthread: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lX11: command not found
../libtool: line 2558: X-llua5.1: command not found
../libtool: line 2558: X-lXext: command not found
../libtool: line 2558: X-lXdamage: command not found
../libtool: line 2558: X-lXfixes: command not found
../libtool: line 2558: X-lXft: command not found
../libtool: line 2558: X-lfontconfig: command not found
../libtool: line 2558: X-lglib-2.0: command not found
../libtool: line 2558: X-lrt: command not found
../libtool: line 5193: Xgcc "" "" "" "" "" "" -o @OUTPUT@ conky-conf_cookie.o conky-colours.o conky-common.o conky-conky.o conky-fs.o conky-hddtemp.o conky-apcupsd.o conky-linux.o conky-top.o conky-diskio.o conky-users.o conky-sony.o conky-mail.o conky-mixer.o conky-mpd.o conky-libmpdclient.o conky-moc.o conky-libtcp-portmon.o conky-tcp-portmon.o conky-llua.o conky-timed_thread.o conky-mboxscan.o conky-x11.o conky-fonts.o conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-algebra.o  -lpthread -lm -lX11 -llua5.1 -lXext -lXdamage -lXfixes -lXft -lfontconfig -lglib-2.0 -lrt: command not found
../libtool: line 5194: Xgcc "" "" "" "" "" "" -o @OUTPUT@ conky-conf_cookie.o conky-colours.o conky-common.o conky-conky.o conky-fs.o conky-hddtemp.o conky-apcupsd.o conky-linux.o conky-top.o conky-diskio.o conky-users.o conky-sony.o conky-mail.o conky-mixer.o conky-mpd.o conky-libmpdclient.o conky-moc.o conky-libtcp-portmon.o conky-tcp-portmon.o conky-llua.o conky-timed_thread.o conky-mboxscan.o conky-x11.o conky-fonts.o conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-algebra.o  -lpthread -lm -lX11 -llua5.1 -lXext -lXdamage -lXfixes -lXft -lfontconfig -lglib-2.0 -lrt: command not found

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

../libtool: line 5203: : command not found
make[3]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/src'
/bin/bash ../libtool --tag=CC   --mode=link gcc -I/usr/include/lua5.1       -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W  -lpthread -lm  -o conky  conky-conf_cookie.o   conky-colours.o conky-common.o conky-conky.o  conky-fs.o conky-hddtemp.o conky-apcupsd.o conky-linux.o conky-top.o conky-diskio.o conky-users.o conky-sony.o  conky-mail.o conky-mixer.o conky-mpd.o conky-libmpdclient.o conky-moc.o  conky-libtcp-portmon.o conky-tcp-portmon.o    conky-llua.o conky-timed_thread.o conky-mboxscan.o conky-x11.o conky-fonts.o   conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-algebra.o    -lm -lX11    -llua5.1    -lXext   -lXdamage -lXfixes   -lXft -lfontconfig   -lglib-2.0   -lrt
../libtool: line 827: X--tag=CC: command not found
../libtool: line 860: libtool: ignoring unknown tag : command not found
../libtool: line 827: X--mode=link: command not found
../libtool: line 994: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 995: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 2239: X-I/usr/include/lua5.1: No such file or directory
../libtool: line 2239: X-I/usr/include/freetype2: No such file or directory
../libtool: line 2239: X-I/usr/include/glib-2.0: No such file or directory
../libtool: line 2239: X-I/usr/lib/glib-2.0/include: No such file or directory
../libtool: line 2239: X-Wall: command not found
../libtool: line 2239: X-W: command not found
../libtool: line 2408: Xconky: command not found

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

../libtool: line 2420: Xconky: command not found
../libtool: line 2558: X-lpthread: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lX11: command not found
../libtool: line 2558: X-llua5.1: command not found
../libtool: line 2558: X-lXext: command not found
../libtool: line 2558: X-lXdamage: command not found
../libtool: line 2558: X-lXfixes: command not found
../libtool: line 2558: X-lXft: command not found
../libtool: line 2558: X-lfontconfig: command not found
../libtool: line 2558: X-lglib-2.0: command not found
../libtool: line 2558: X-lrt: command not found
../libtool: line 2558: X-lpthread: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lX11: command not found
../libtool: line 2558: X-llua5.1: command not found
../libtool: line 2558: X-lXext: command not found
../libtool: line 2558: X-lXdamage: command not found
../libtool: line 2558: X-lXfixes: command not found
../libtool: line 2558: X-lXft: command not found
../libtool: line 2558: X-lfontconfig: command not found
../libtool: line 2558: X-lglib-2.0: command not found
../libtool: line 2558: X-lrt: command not found
../libtool: line 2558: X-lpthread: command not found
../libtool: line 2558: X-lm: command not found
../libtool: line 2558: X-lX11: command not found
../libtool: line 2558: X-llua5.1: command not found
../libtool: line 2558: X-lXext: command not found
../libtool: line 2558: X-lXdamage: command not found
../libtool: line 2558: X-lXfixes: command not found
../libtool: line 2558: X-lXft: command not found
../libtool: line 2558: X-lfontconfig: command not found
../libtool: line 2558: X-lglib-2.0: command not found
../libtool: line 2558: X-lrt: command not found
../libtool: line 5193: Xgcc "" "" "" "" "" "" -o @OUTPUT@ conky-conf_cookie.o conky-colours.o conky-common.o conky-conky.o conky-fs.o conky-hddtemp.o conky-apcupsd.o conky-linux.o conky-top.o conky-diskio.o conky-users.o conky-sony.o conky-mail.o conky-mixer.o conky-mpd.o conky-libmpdclient.o conky-moc.o conky-libtcp-portmon.o conky-tcp-portmon.o conky-llua.o conky-timed_thread.o conky-mboxscan.o conky-x11.o conky-fonts.o conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-algebra.o  -lpthread -lm -lX11 -llua5.1 -lXext -lXdamage -lXfixes -lXft -lfontconfig -lglib-2.0 -lrt: command not found
../libtool: line 5194: Xgcc "" "" "" "" "" "" -o @OUTPUT@ conky-conf_cookie.o conky-colours.o conky-common.o conky-conky.o conky-fs.o conky-hddtemp.o conky-apcupsd.o conky-linux.o conky-top.o conky-diskio.o conky-users.o conky-sony.o conky-mail.o conky-mixer.o conky-mpd.o conky-libmpdclient.o conky-moc.o conky-libtcp-portmon.o conky-tcp-portmon.o conky-llua.o conky-timed_thread.o conky-mboxscan.o conky-x11.o conky-fonts.o conky-specials.o conky-tailhead.o conky-temphelper.o conky-text_object.o conky-algebra.o  -lpthread -lm -lX11 -llua5.1 -lXext -lXdamage -lXfixes -lXft -lfontconfig -lglib-2.0 -lrt: command not found

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

../libtool: line 5203: : command not found
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/src'
make[2]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/src'
make[1]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/src'
Making install in doc
make[1]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/doc'
make[2]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './conky.1' '/usr/local/share/man/man1/conky.1'
make[2]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/doc'
make[1]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/doc'
Making install in lua
make[1]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/lua'
make[2]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/lua'
test -z "/usr/local/lib/conky" || /bin/mkdir -p "/usr/local/lib/conky"
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/lua'
make[1]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/lua'
Making install in data
make[1]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/data'
make[2]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/data'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/etc/conky" || /bin/mkdir -p "/usr/local/etc/conky"
 /usr/bin/install -c -m 644 'conky.conf' '/usr/local/etc/conky/conky.conf'
 /usr/bin/install -c -m 644 'conky_no_x11.conf' '/usr/local/etc/conky/conky_no_x11.conf'
make[2]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/data'
make[1]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2/data'
make[1]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2'
make[2]: Entering directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2'
make[1]: Leaving directory `/home/jelopez/Desktop/Instaladores/Conky/conky-1.7.2'


```

what am i missing .. it must be a lot im sure .. 


Thanks in advance :)

---

### Post by miegiel on 2009-10-09
just a thought: did you uninstall the old conky 1st ?

---

### Post by Kaizzer on 2009-10-09
emm nup ..  do i need to ? 
probably another newbie question from me.. but .. how do i do that ? (uninstall) 
thanks.

---

### Post by miegiel on 2009-10-09
> **Kaizzer said:**
> emm nup ..  do i need to ? 
probably another newbie question from me.. but .. how do i do that ? (uninstall) 
thanks.

Open a terminal and do
```
sudo apt-get -s remove conk
```
Don't hit *Enter*, but hit *Tab* once, twice or 3 times. This will show you a list of packages starting with *conk* wich you can uninstall. The *-s* makes it a simmulation so nothing is installed yet ;)
I get
```
sudo apt-get -s remove conky
conky      conky-all
```
Next simulate uninstalling both packages :
```
sudo apt-get -s remove [COLOR="Blue"]conky conky-all[/COLOR]
```
Read the output, if you're confident no essential packages will be removed, run the line again without the *-s* to uninstall it for real.
```
sudo apt-get remove [COLOR="Blue"]conky conky-all[/COLOR]
```
(replace the [COLOR="Blue"]blue bits[/COLOR] with the packages you found)

---

### Post by Kaizzer on 2009-10-09
i need a guide here ... this is what i get .. 

```
jelopez@jelopez-laptop:~/Desktop/Instaladores/Conky/conky-1.7.2$ sudo apt-get -s remove conky 
Display all 1217 possibilities? (y or n)
acl                                         libespeak1                                  linux-generic
acpi                                        libexchange-storage1.2-3                    linux-headers-2.6.24-16
acpid                                       libexempi3                                  linux-headers-2.6.24-16-generic
acpi-support                                libexif12                                   linux-headers-2.6.24-24
adduser                                     libexpat1                                   linux-headers-2.6.24-24-generic
alacarte                                    libexpat1-dev                               linux-headers-generic
alsa-base                                   libffi4                                     linux-image-2.6.24-16-generic
alsa-utils                                  libflac8                                    linux-image-2.6.24-24-generic
ample                                       libflickrnet2.1.5-cil                       linux-image-generic
amsn                                        libfontconfig1                              linux-libc-dev
anacron                                     libfontconfig1-dev                          linux-restricted-modules-2.6.24-16-generic
apmd                                        libfontenc1                                 linux-restricted-modules-2.6.24-24-generic
apparmor                                    libfreetype6                                linux-restricted-modules-common
apparmor-utils                              libfreetype6-dev                            linux-restricted-modules-generic
app-install-data                            libfribidi0                                 linux-sound-base
app-install-data-commercial                 libfs6                                      linux-ubuntu-modules-2.6.24-16-generic
apport                                      libfuse2                                    linux-ubuntu-modules-2.6.24-24-generic
apport-gtk                                  libgadu3                                    locales
apt                                         libgail18                                   logrotate
aptitude                                    libgail-common                              lsb-base
apturl                                      libgail-gnome-module                        lsb-release
apt-utils                                   libgamin0                                   lshw
aspell                                      libgc1c2                                    lsof
aspell-en                                   libgcc1                                     ltrace

```

not sure to uninstall...

---

### Post by miegiel on 2009-10-09
try again ;) *conk* without the *Y*
```
sudo apt-get -s remove conk
```

---

### Post by Kaizzer on 2009-10-09
hmm nup .. same result .

```

jelopez@jelopez-laptop:~/Desktop/Instaladores/Conky/conky-1.7.2$ sudo apt-get -s remove conk 
Display all 1217 possibilities? (y or n)
acl                                         libespeak1                                  linux-generic
acpi                                        libexchange-storage1.2-3                    linux-headers-2.6.24-16
acpid                                       libexempi3                                  linux-headers-2.6.24-16-generic
acpi-support                                libexif12                                   linux-headers-2.6.24-24
adduser                                     libexpat1                                   linux-headers-2.6.24-24-generic
alacarte                                    libexpat1-dev                               linux-headers-generic
alsa-base                                   libffi4                                     linux-image-2.6.24-16-generic
alsa-utils                                  libflac8                                    linux-image-2.6.24-24-generic
ample                                       libflickrnet2.1.5-cil                       linux-image-generic
amsn                                        libfontconfig1                              linux-libc-dev


```

---

### Post by miegiel on 2009-10-09
Do you have a space at the end of the line? It looks like all your installed packages are listed (1691 in my case).

---

### Post by Kaizzer on 2009-10-09
yup on first tab it autocomplete   conk to .. conky and space .. an then list everything else.. i looked at the list and there is only conky .. to uninstall 
so .. 
should i proceed uninstalling ?

---

### Post by miegiel on 2009-10-09
> **Kaizzer said:**
> yup on first tab it autocomplete   conk to .. conky and space .. an then list everything else.. i looked at the list and there is only conky .. to uninstall 
so .. 
should i proceed uninstalling ?

That means the only package starting with *conk* is *conky* (sorry should have realized that sooner).

run
```
sudo apt-get -s remove conky
```
to simulate and
```
sudo apt-get remove conky
```
to uninstall

---

### Post by Kaizzer on 2009-10-09
oooooooookey .. done it :) 
now .. to compile the new version .. 
uhmm im scared:)

---

### Post by Kaizzer on 2009-10-09
and ..nup!! .. same erroroes that shows in Post 1..

---

### Post by miegiel on 2009-10-09
> **Kaizzer said:**
> and ..nup!! .. same erroroes that shows in Post 1..
try removing the */tmp/.X0-lock* make install is moaning about.

```
rm /tmp/.X0-lock
```
or
```
sudo rm /tmp/.X0-lock
```
if you need permission

---

### Post by miegiel on 2009-10-09
That didn't kill your ubuntu did it !?

---

### Post by Kaizzer on 2009-10-09
well something like that .
i used the following command line .. sudo checkinstall  i did generate a .dev file ..  in this process .. same errors appears as in post n° 1 .. but as i said .. it generated the .dev .. so .. i tryed to installed .. 

sudo dpkg -i conky-whatever.dev .. 
and nothing much happend .. 

on console .. conky shows .as not existent .. so .. i did re-compile .. and .. it crashes like hell .. 

so.. im still stuck ..

---

### Post by miegiel on 2009-10-09
I don't really have ideas any more, kind of hoping someone who knows more about compiling will post something.

Well there is 1 idea, but I'm afraid to make things worse. I'm really sorry that your ubuntu is crashing :(

Just wondering, why are you still using hardy?

---

### Post by slakkie on 2009-10-09
> **miegiel said:**
> I don't really have ideas any more, kind of hoping someone who knows more about compiling will post something.

Well there is 1 idea, but I'm afraid to make things worse. I'm really sorry that your ubuntu is crashing :(

Just wondering, why are you still using hardy?

Hardy is LTS and still supported by both community and Canonical.

Anyways, to the OP. What did you do before you configured conky?

What you should do is:

```

sudo aptitude install checkinstall
sudo apt-get build-dep conky
mkdir $HOME/conky
cd $HOME/conky
wget http://downloads.sourceforge.net/project/conky/conky/1.7.2/conky-1.7.2.tar.gz?use_mirror=mesh
tar zxvf conky-1.7.2.tar.gz
cd conky-1.7.2
./configure --help | less # check which options you want to enable/disable
./configure --prefix=/opt/conky 
make
make test
sudo checkinstall make install 

```

This is how you would compile conky from source code, or any other package for that matter.

---

### Post by Kaizzer on 2009-10-13
slakkie.. thanks for your post.

ill try to do as you say later on this evening .. ill post my results.. 
TIA

---

