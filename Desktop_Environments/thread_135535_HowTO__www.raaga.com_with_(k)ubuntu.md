---
title: "HowTO : www.raaga.com with (k)ubuntu"
date: 2006-02-24
forum: Desktop Environments
---

### Post by abhaysahai on 2006-02-24
Hi,
After months of windowing just to listen to songs from raaga.com, I
finally got a Linux alternative. Though it is not a native Linux one,
but works never the less. 
OK It is not an orignal idea by me, but a borrowed/stolen one. But being
a nice thief ( Robinhood), I belive in sharing that idea with all. 
Here it goes ::

Some sites like [www.raaga.com](www.raaga.com) do not work in spite of having
the latest real player and the corresponding firefox plugins, even
mplayer plugins do not work. I've tried my best, but there seems to be
no way of getting them to work, so I had to use a workaround. Do this
only if there are some sites which do not work, otherwise you should be
all set.

    * Download and install wine. I am using the latest wine using 
          deb  [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

    * Run #wine. It will create default directories, etc.
    * Copy this file as your wine
[config]("http://www.cs.cornell.edu/~scs49/config.txt") file,
i.e. save it as ~/.wine/config
    * Download the
[URL="http://www.mozilla.org/products/firefox/all"]windows installer of
firefox[/URL] and install it by opening it with wine. Start it using
wine (You may have to give a command like #
wine /home/abhaysahai/.wine/drive_c/Program\ Files/Mozilla\
Firefox/firefox.exe , and install realplayer (windows version) from
[www.real.com](www.real.com) through it. (At the end of installation, real
player hangs, but after restarting ( or kill the process associated with
real player-- dont know kill, restart) , everything works ok for me).
    * Now this installation of firefox should be able to play all sorts
of internet radios, etc. (At least, it plays raaga.com and smashits.com
for me!)
    * If you find a better solution,
[EMAIL="abhaysahai@gmail.com"]Please do let me know![/EMAIL]

Want the orignal link -- yes it has more, actually much more info

[http://www.cs.cornell.edu/~scs49/install_linux.html#destHeader164](http://www.cs.cornell.edu/~scs49/install_linux.html#destHeader164)

And yes even the sites like hsbc.co.in works with this trick. 
How was my version ( did u say coppied or lifted version ?? :mad: )

Abhay
\\:D/

---

### Post by rado_london on 2006-02-24
Nice one, why dont you move it to the Customizitaon section!

---

