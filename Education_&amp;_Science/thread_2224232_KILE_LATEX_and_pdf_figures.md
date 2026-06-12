---
title: "KILE LATEX and pdf figures"
date: 2014-05-15
forum: Education &amp; Science
---

### Post by nepomo on 2014-05-15
Hi,

I run into a strange problem with kile and my current writing. I am including images using the following code

```

\begin{figure}[h]
 \centering
 \includegraphics[width=.5\linewidth]{images/layout}
 \caption{bla}
 \label{fig:layout}
\end{figure}
```

and then run pdflatex. This worked perfectly fine on some old pdf images I had in the images folder. Now I am trying to get one more (new) image in and copied the code above and the only thing altered is the image name. 

However, now pdflatex gives me the error that it cannot find the file name. It is present in the folder and it does have the same permissions as all the other already (present) pdf files. The new one was created in matlab and using export_fig to render the pdf image directly from the .fig file.

I have no solution and tried everything I could think of. Why is this pdf image to the others. Apparently it must be different, since it is the only one not working. I imported it in gimp and saved it as a new pdf thinking it might have something to do with export_fig.m, no success. 

To define the path with pathtographics did not help, also copying the file to the .tex file directory did not make a difference. 

I am using the shell escape and even on the console it is not working. 

Any help on this issue would be greatly appreciated since currently my whole workflow stopped due to the fact that I cannot use new images.


Cheers.

---

### Post by nepomo on 2014-05-15
Hi,

after several more hours messing around and trying minimal working examples without success. I had the idea that it might be related to the fact that I use the main tex file and everything including images and figures on a external USB drive. I copied the whole folder to the hard drive and it worked. 

I have no idea why this one now works and if anyone could offer a suggestion I would still be happy to know how and why that appears to solve the problem. 
After all defining the graphics path should have solved that problem I reckon.... but it did not. 

Thanks.

---

