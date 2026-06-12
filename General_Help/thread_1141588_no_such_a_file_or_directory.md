---
title: "no such a file or directory"
date: 2009-04-28
forum: General Help
---

### Post by yos on 2009-04-28
[SIZE=2]Hi, 

Please Can some one help me.
When I run a program in C++ I type this command 
 yosra@yosra-desktop:~/Bureau/paradiseo-1.2.1/paradiseo-eo/src/FeatureSelection2$ ./FeatureSelectionEA 
I have this results: 
No such file or directory
Do you think that is it due to the acces permission?
yosra@yosra-desktop:~/Bureau/paradiseo-1.2.1/paradiseo-eo/src/FeatureSelection2$ ls -l 
total 8112
drwx------ 2 yosra yosra    4096 2006-11-21 09:28 data
-rw-r--r-- 1 yosra yosra    1888 2006-05-21 21:30 eoFeatureSelectionEvalFunc.h
-rw-r--r-- 1 yosra yosra    2806 2006-03-28 15:38 eoFeatureSelection.h
-rw-r--r-- 1 yosra yosra    1682 2006-05-21 17:17 eoFeatureSelectionInit.h
-rw-r--r-- 1 yosra yosra    2047 2006-05-21 18:41 eoFeatureSelectionMutation.h
-rw-r--r-- 1 yosra yosra    2180 2006-05-21 18:40 eoFeatureSelectionQuadCrossover.h
-rw-r--r-- 1 yosra yosra    3641 2006-05-21 18:37 eoFeatureSelectionQuadCrossoverSSOCF.h
-rwxr-xr-x 1 yosra yosra 2903174 2009-04-28 20:22 FeatureSelectionEA
-rw-r--r-- 1 yosra yosra    5764 2006-05-21 21:46 FeatureSelectionEA.cpp
-rw-r--r-- 1 yosra yosra 3104200 2009-04-23 14:17 FeatureSelectionEA.o
-rw-r--r-- 1 yosra yosra    3274 2009-04-27 18:29 FeatureSelectionEA.status
-rw-r--r-- 1 yosra yosra    3274 2006-05-21 21:51 FeatureSelectionEA.status~
-rw-r--r-- 1 yosra yosra    5313 2009-04-27 14:46 #FeatureSelectionLibEA.cpp#
-rw-r--r-- 1 yosra yosra    5314 2009-04-27 14:42 FeatureSelectionLibEA.cpp
-rw-r--r-- 1 yosra yosra    5312 2006-03-17 11:03 FeatureSelectionLibEA.cpp~
-rwxr-xr-x 1 yosra yosra 2091387 2006-05-15 17:07 leukemia_all.data
-rw-r--r-- 1 yosra yosra    5230 2006-03-17 11:03 make_FeatureSelection.cpp
-rw------- 1 yosra yosra    1961 2009-04-23 14:09 Makefile
-rw-r--r-- 1 yosra yosra    1656 2006-05-21 18:08 Makefile~
-rw-r--r-- 1 yosra yosra    3044 2006-03-17 15:48 make_genotype_FeatureSelection.h
-rw-r--r-- 1 yosra yosra    8445 2006-03-20 09:58 make_op_FeatureSelection.h
-rw-r--r-- 1 yosra yosra    7860 2006-05-21 21:31 objectif.h
-rw-r--r-- 1 yosra yosra   73904 2009-04-23 14:17 svm.o
Please I need your help.
Best regards.[/SIZE]

---

### Post by 3Miro on 2009-04-28
That is odd. Permissions are fine, so there is something else going on.

Try typing ./F and then press tab twice. Then keep on adding info one character at a time and pressing tab to make sure something did not get misspelled.

---

### Post by yos on 2009-04-28
Thanks 3Miro for your help I try what did you say and I have still this error :(
yosra@yosra-desktop:~/Bureau/paradiseo-1.2.1/paradiseo-eo/src/FeatureSelection2$ ./FeatureSelectionEA 
Loading model from file ...
No such file or directory
Please help me I don't know what the error. So when I run the same results on the fedora7 I haven't any problem. the problme is it with ubuntu?

---

### Post by 3Miro on 2009-04-28
We have to read carefully:
```

osra@yosra-desktop:~/Bureau/paradiseo-1.2.1/paradiseo-eo/src/FeatureSelection2$ ./FeatureSelectionEA 
```
is when you evoke the program. Then the next thing that happens is:
```
Loading model from file ...
```
and only afterwards:
```
No such file or directory
```

The file that is missing is not the FeatureSelectionEA. That one exists and is running. The program is looking for another file, something about a model, I don't know what that is. Check with fedora and see if there are any "model" files.

How did you install the program, if you just copied it from fedora7, it is possible that you missed copying something.

---

### Post by yos on 2009-04-28
yes I copied it from fedora7, but I don't think that I had missed a model. I will try again and will say what I have.

---

### Post by 3Miro on 2009-04-28
Maybe something in the data folder. It looks a reasonable place to look.

---

### Post by yos on 2009-04-28
The data folder contains only one file that is leukemia_all.data, for that I think is it here the problem.
I attache the makefile maybe it contains something wrong!:confused:
I'm so confused please help me!:(

---

### Post by 3Miro on 2009-04-28
First of all you should check for the permissions of the file (it needs to have r in the left most triple).

Then (an I suspect the permissions are OK), you have to call the program the proper way. How do you do that in Fedora. The makefile contains a test case where the program is called with parameters:
```

./FeatureSelectionEA data/leukemia_all.data -w 1 FeatureSelectionEA.status

```

If that does not work, try simply:
```

./FeatureSelectionEA data/leukemia_all.data -w 1

```

If that does not work, check how the thing is being called under Fedora.

---

### Post by yos on 2009-04-28
I have done what did you say for me and nothing runs :(

       ./FeatureSelectionEA data/leukemia_all.data -w 1
No such file or directory
 
I don't understand what's wrong?

---

### Post by stoneage on 2009-04-28
Did you check the file is executable?

---

### Post by 3Miro on 2009-04-28
The file is executable (according to the first post).

There might be differences in the way Ubuntu and Fedora run (actually there are differences, the question is what exactly).

Can you recompile the thing under Ubuntu?

---

### Post by yos on 2009-04-29
yes stoneage it's an executable file!

---

### Post by yos on 2009-04-29
3Miro I recompile the executable file under ubuntu and under fedora this time I have the same error : no such file or directory:confused::confused::confused:
I don't understand what's the problem?

---

### Post by Futurian on 2010-06-09
Did anyone ever get anywhere with this? If so, how?
I'm trying to use paradiseo (in Lucid), and can't get make to work.

Thanks.

---

