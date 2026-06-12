---
title: "Augmented Reality: a practicle guide examples not working on ubuntu"
date: 2009-08-30
forum: Desktop Environments
---

### Post by Captain_Glen on 2009-08-30
Hi,

I recently bought the book: Augmented Reality: A Practicle Guide ([http://pragprog.com/titles/cfar/augmented-reality](http://pragprog.com/titles/cfar/augmented-reality)).  It has example code that it says runs on Windows, MacOS and Linux.

You can download the code here: ([http://pragprog.com/titles/cfar/source_code](http://pragprog.com/titles/cfar/source_code))

But I can't get the binaries to run.  Has anyone got this book and got the binaries to run on ubuntu?

I also can't figure out how to compile the examples in Ubuntu.  How would I do this?

Here is what it says to do:

Compiling for Linux
 Refreshingly, there are no changes required to get the programs in this
 chapter to compile for Linux, but as with Windows, you’ll first have to
 find your GL and GLUT files. This may mean you’ll have to download
 the correct version of GLUT for your machine.
 You need to link in the GL, GLU, and GLUT libraries and provide a path
 to the GLUT header file and the files it includes. See whether there is
 a glut.h file in the /usr/include/GL directory; otherwise, look elsewhere for it—you could use the command find / -name "glut.h" to search your entire
 machine, or you could use the locate command (locate glut.h).
 You may need to customize the paths, but here is an example of the
 compile command:
 gcc -o opengl_template opengl_template.cpp -I /usr/include/GL
       -I /usr/include -lGL -lGLU -lglut
 gcc is a C/C++ compiler that should be present on your Linux or Unix
 machine. The -I /usr/include/GL command-line argument tells gcc to look
 in /usr/include/GL for the include files. In this case, you’ll find glut.h and
 what it includes. When linking in libraries with gcc, you use the -lX
 switch—where X is the name of your library and there is a correspond-
 ing libX.a file somewhere in your path. For this example, you want to
 link in the library files libGL.a, libGLU.a, and libglut.a, so you will use the
 gcc arguments -lGL -lGLU -lglut. These three files are found in the default
 directory /usr/lib/, so you don’t need to specify their location as you did
 with glut.h. If you did need to specify the library path, you would add -L
 to the path.
 To run your compiled program, type ./opengl_template or, if the current
 directory is in your shell’s paths, just opengl_template.

When working in Linux, it’s important to know that you may need to
keep your texture files to a maximum of 256 by 256 pixels or find the
settings in your system to raise this limit. Often an OpenGL program
will work in Windows but produce a blank white texture in Linux until
the texture size is reduced.

The above instructions make no sense to me.  Do I have to use gcc to compile or can I use eclipse?

If I use either eclipse or gcc what do I need to do to compile and run the program?

---

### Post by ckonestroh on 2009-08-30
[COLOR="Red"][SIZE="5"]
This book is not for beginners [/SIZE][/COLOR][COLOR="Teal"]this is starting to lean more towards an intermediate level of understanding...[/COLOR]

   Programmer also states the video will not run if screen size goes beyond limits so he expresses changing fx and fy of camera... Programmer puts the necessary source files in a folder in order to run the program...


These are rough samples for Experienced Programmers who want to build video games, visual effects and the ideas are endless for Experienced Programmer...

Now if you don't understand following statements more then likely you wont get the program to work....

1. if else
2. if return
3. if for
4 matrix
5. else if
6. library's
7. pointing to files/libs
8. camera angles and setup's
9. what program(vlc player, firefox, windows player) will run the following  programs...
10. he also refers to the use of web cam....



Now I don't know your level of computer programming, but this is for a seasoned programmer...

If you are an inexperienced programmer your going to want to go to a forum where you can talk to an experienced programmer for advice on learning the list of above ideas....


later...

Good Luck...

P.S Programming takes a lot of trial and error...
 

I wish you the best

---

