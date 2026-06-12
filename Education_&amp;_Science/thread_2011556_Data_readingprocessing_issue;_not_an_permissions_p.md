---
title: "Data reading/processing issue; not an permissions problem"
date: 2012-06-27
forum: Education &amp; Science
---

### Post by moonbees on 2012-06-27
Hello all,

New to Linux/programming and to these forums, and it seems like a wonderful community on both counts. Therefore, please forgive anything ignorant or silly herein contained; I'm still learning!

I'm currently running v. 11.10 on a VirtualBox VM on my mac to do some analysis on eye position data gathered from an eye-tracking camera. The programs I'm using to do this are binary executable files (originally written in C, I believe) made by another researcher who, for various reasons, I can no longer pester for help with this issue. Thus I've come to you!

These executables read data from from files with special extensions that specify the kind of data they contain. He provided me with a set of sample data and with the executables, and I can get those to run just fine on the data he gave me. We're hoping to use these programs on data we've collected, but for the life of me, I just can't get them to work. I'll try and explain in greater detail.

We collect the data with MATLAB (on a mac), and it is stored in a data-structure in .m output files for each trial. I've written a matlab script that will export the data in what I believe is the appropriate format. I've used text editors on my mac and VIM in Linux to try and find any differences with  text formatting for the data itself, and it appears to be all the same. The MATLAB script also appends the correct extensions to the files as they are generated. 

The problem I'm having is that when I run the same executable on two different data files (his and ours), it will read both files and generate an output file for both, correctly. However, when the executable is run our data file, the output file contains **no** data. The correct header information is printed at the top of the file, but there's nothing else in them. I thought this might be a problem with one of the executables, or with that particular data sample, but I've now run all of the executables he provided on dozens of samples, and I can't get them to actually print any data. 

My question is: where do I start looking for the source of this problem, and does this sound like something that will actually have a solution? Given the fact that these data files are passed through several computers, between many different programs and then into a virtual machine running an entirely different operating system, I'm sure it's possible that something slipped. But where do I start looking? I thought that it might be a problem with permissions or something, but those are all the same for both our data and the sample data. 

](*,)

Any thoughts? Questions you have that might clarify the situation? Please let me know!

Thanks again!

---

### Post by steeldriver on 2012-06-27
Well since you mention different OSes the most obvious wild guess would be it's something to do with DOS versus UNIX line termination (CR/LF versus LF)

Beyond that, if you can generate EXACTLY the same data, then you could use 'diff' which may find some subtle differences that you missed by eye (especially if the files are large)

Do you have the source code for the executables? are there any debug/verbose options you can invoke at the command line?

Alternatively you could go at it the other way i.e. take some of the working example files and try to import them into Matlab (and then back out to test your converter)

---

### Post by moonbees on 2012-06-27
steeldriver,

Thanks for your speedy reply. I'll reply in order to your remarks:

1). Using dos2unix on one of my data files and re-running the executables on it; I'm still encountering the same failure. Also tried using the 'flip' command as well, also no effect.

2). Can't use diff, as the data is taken from two different experiments; just returns that every line is different. 

3). Have the source, but not too sure what to do with it. See below an example for one of the executables (the first in the processing workflow, so a likely candidate for the source of the problem):

\code
/// SaccadeDetector *sacDet = new SaccadeDetector(gazeSource, 
///     screenGeometry, videoWidth, videoHeight, parameters,
///     DataReader<GazeCoord>::MODE_FREEWHEEL);
/// ...
/// while(!sacDet->FEndOfStream())
/// {
///     sacDet->AdvanceToNextSaccade();
///
///     SaccadicGazeSample onset  = sacDet->CurrentSaccade().onset;
///     SaccadicGazeSample offset = sacDet->CurrentSaccade().offset;

The phrase 'Datareader<gazecoord>::MODE_FREEWHEEL' jumps out at me, but I'm not sure what this/where it is located/whether it's editable in Linux (again, apologies for ignorance.) I'm also not sure what those three periods in line 4 represent--are they meaningful in C, or was he perhaps just condensing his code to the parts relevant to this executable? Again, a lot I don't know.

4). I'll definitely try putting some of the working files into MATLAB and then exporting them with my converter. 

Thanks for the help!

---

### Post by steeldriver on 2012-06-27
Did you copy that literally? if so and it's C/C++ that whole section is commented out (//). My C++ is limited but

```
DataReader<GazeCoord>::MODE_FREEWHEEL
```looks like it is probably just a reference to a class constant for a templated DataReader class, I wouldn't worry too much about that.

I will help if I can - I have an interest in biometrics

---

### Post by moonbees on 2012-07-09
Steeldriver,

We sorted this out-- the problem had to do with some information associated with the timestamp on each datapoint. Easily fixed.

Thanks for your help!

---

