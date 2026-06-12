---
title: "My PCSX won't run the file .img"
date: 2013-02-14
forum: Gaming &amp; Leisure
---

### Post by Dacifer on 2013-02-14
I've  got a  problem.

I used to be able to run my .img  files on the pcsx, but las  night i tried to run a  file .ccd, and it  crashed, after  that it wont let  me run any other file (even the .img  that worked previously)

I tried  UN-installing  and installing again but it wont do. when I tried to run an .img file, at the terminal appeared the next message: "RGB & YUV not found. Quitting."

any idea what to do?

---

### Post by Dacifer on 2013-02-14
I tried changing  my video plug-in to opengl and when i tried to run an .img file,  the message  in the terminal, was  this:

"The program 'pcsx' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 12 error_code 1 request_code 153 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"

but  I’m not  sure what does this mean

---

### Post by LillyDragon on 2013-02-16
I don't have any experience with the IMG format, but it couldn't hurt to rip your game again in BIN/CUE or BIN/TOC format and see if it's still compatible. (And alternatively, if your game doesn't have any Audio data tracks, ripping it as an ISO would also be a better idea, and more convenient since it's all in one file.)

Compatibilty with some games still isn't perfect on PCSX, (I still can't get CD audio playback to behave on Vib Ribbon, for instance.) and if IMG support is somehow flaky, that's only going to add to your problems.

Also, does your IMG file come with a CUE sheet or TOC? Having that file in the game's directory is pretty important, and if you renamed your game image, you'll have to manually rename references to the IMG file in your CUE or TOC with a text editor as well.

---

