---
title: "Neverwinter Nights Movie issues"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by Kalinda on 2007-06-04
Okay, I followed leech's howto, although I'm using the original NWN and not the crazy Platinum one.

To start with, the tarball I downloaded with nwnmovies in it didn't even have the movie files, so it couldn't find them.. so I pulled them off the CD and placed them in the movies folder, which I had to create. Now, doing this made me able to play the movies in Bink from the terminal... it worked nicely.

But not in the game. When I loaded, it played the AtariLogo and then the whole thing sat there with a black screen.. (had to restart the X server to do anything) Well, I then deleted the movie files for the intro because I just wanna watch the ones between chapters to better follow the plot.

After that I went to watch the prelude movie from the menu and it started playing after a bit of lag.. but I have no sound :O When I hit ESC, it did the black screen thing again.

Looking at the log file reveals the following:

```
./nwmovies.pl Prelude >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: Prelude: Mon Jun  4 16:29:50 2007
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/prelude.bik
1180988990.893964: BinkLib: SDL_PRELOAD Initialized
mcop warning: user defined signal handler found for SIG_PIPE, overriding
pure virtual method called
terminate called without an active exception
```

I know the last line is because I hit escape.. but I've no idea what the other stuff means. Sound works within the game itself.. and the game works flawlessly otherwise.

Can anyone help? leech, you out there?

Thanks :)

EDIT: Okay, I now know it's because the stuff tries to use Arts, since I run KDE, but I guess Arts doesn't work for the movie sound.. so I added this to my nwn script: 

/usr/bin/artsshell -q suspend
export SDL_AUDIODRIVER=alsa

It at least stopped the black screening.. but now I have no sound period because Bioware's SDL doesn't support alsa. If I remove the .lib from the SDL path in the script, the movies don't work at all.. so now I assume I must find out what sound architectures Bioware's SDL does support..

---

