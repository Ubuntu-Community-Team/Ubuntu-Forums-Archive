---
title: "How can I compare multiple images using GuiOctave?"
date: 2012-09-13
forum: Education &amp; Science
---

### Post by sneeuwman74 on 2012-09-13
Hi there,

I have a question. I sincerely hope anyone can help me!

For a new project of mine, I'm looking for a way to compare almost identical images. Imagine, I've got 100 images which all look quite the same, but most of them are not. Just some of the images are identical. I know that. And with the naked eye it's impossible to find out which ones are identical. Now I'm looking for a way to use software to find out. So that a program tells me after scanning all of the images: 
- Image 1, 34 and 99 are identical. 
- Image 2, 23, 76 and 89 are identical. 
- Image 3 is not identical to any other image. 
- Image 4 and 100 are identical.
- ... and so on. 

A guy told me i should use GuiOctave. So after installing the software I was like: "Uhm... Okay. Now what?" I'm working as an artist, and not as a computerexpert  So i hope you can imagine I haven't got the slightest clue of what I'm supposed to do. 

Can anyone help me solve this puzzle? 

BTW, if anyone knows of any other, easier ways maybe, please be my guest :-)

Thank you very much!

Best Regards,
Barry
sneeuwman74

---

### Post by mevun on 2012-09-13
I think the guy who mentioned that Gui Octave program thought you  should do a "correlation" between the files.  That is a signal  processing method which can calculate how close two signals are.  People  who know how to do that generally have college degrees in a technical  field like electrical engineering.  I'm guessing you don't, or else you  would probably have understood why he suggested that tool.

If the image files are identical in their actual data bits but have different names, then you can do a file comparison.  For that, you need a "checksum" program which will compute a number that is based on all the data bits in the file.  I think Linux command line has "cksum" program for that.  You'd still need some logic to compare the generated checksums, but the general algorithm would be:

For each file, generate a checksum and store the filename and its checksum in a list.  Then for each filename and checksum in that list, see if any other checksum is the same.  If so, then those files are the same.

Typically, one could write a script to do this for you.

---

### Post by sneeuwman74 on 2012-09-14
Thanks for the information. This actually sounds pretty good! I also found a guy who wants to help me to write this script. I hope it works. 

Thank you!

---

### Post by afz12 on 2012-09-15
Admittedly this might be a bit "abstract" but image comparison isn't straightforward. A direct correlation (2 D) "might" work but can be overly sensitive to small changes. For example, say your images are grey-scale. If two identical images are compared but just have different contrast, the correlation will "say" they are very different. You will need to control for this.

Octave3.2 is probably quite suitable for the task. It may have some tools already available for this. 

Another approach is to convert the images to "spatial frequencies". Octave will do this using its FFT function. FFT's (Fast Fourier Transform) for 1 D data or for images, 2 D data. The output of the FFT can be thought of as keys pressed on a piano - the FFT is usually applied to time domain data (eg as seen on an oscilloscope) and converts this to frequency domain data (e.g. like individual music notes). The analogy is approximate as the FFT output is linearly spaced whilst piano notes are spaced logarithmically.

In Octage or qtOctave the FFT (and its inverse) are includes as standard - almost all analysis software includes these. The idea of "spatial frequency" is no different from "audible frequency" but becomes harder to interpret perhaps in 2 D. However if you transform your data (one line code for FFT(x) ) you have one additional opportunity for comparison. You still need to pre-adjust for contrast I guess, but the comparison of images may be less sensitive to noise effects. Interestingly, 2 D FFT analysis is extremely popular in laser optics but is also applied to understanding brain neural structures allocated for visual recognition of form as well as colour. It may therefore be worth a look given this similarity. However you will probably need someone well versed in technology and mathematical processing, and/or with a degree in Physics, preferably a Masters or PHD. Image comparison is somewhat specialised. 

Your best option is to find software that is already designed to do this.

---

### Post by sneeuwman74 on 2012-09-19
Thank you for your response! 

Hopefully I can find a program especially designed for this. It looks like most of the programs are designed for comparing just two images. And not for comparing bulk. But who knows. I'm on it!

---

