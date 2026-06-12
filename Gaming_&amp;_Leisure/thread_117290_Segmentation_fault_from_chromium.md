---
title: "Segmentation fault from chromium"
date: 2006-01-14
forum: Gaming &amp; Leisure
---

### Post by pinkunicorn on 2006-01-14
I'm trying to run chromium on a machine running breezy (updated from hoary, if that's relevant). I start chromium from the command line and get a window which dies immediately, and then 

> Fatal signal: Segmentation Fault (SDL Parachute Deployed)

in my terminal window.

I've tried running strace on chromium, and that gives me

[... lots of text ...]
> open("/home/henrik/.chromium-score", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 9
> fstat64(9, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
> mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb3a23000
> write(9, "\0\0\0\0\200\204\16A\0\0\0\0\0j\10A\0\0\0\0\200O\2A\0\0"..., 3800) = 3800
> close(9)                                = 0
> munmap(0xb3a23000, 4096)                = 0
> --- SIGSEGV (Segmentation fault) @ 0 (0) ---
> rt_sigaction(SIGSEGV, {SIG_DFL}, {0xb7d9febc, [], 0}, 8) = 0
> write(2, "Fatal signal: ", 14Fatal signal: )          = 14
> write(2, "Segmentation Fault", 18Segmentation Fault)      = 18
> write(2, " (SDL Parachute Deployed)\n", 26 (SDL Parachute Deployed)
[... some more text ...]

It makes no difference whether the highscore file exists or not when I start the game, it still crashes (but the file gets created if it doesn't exist).

I don't get any core file, for some reason, even though I've run "ulimit -c unlimited".

Ideas?

---

