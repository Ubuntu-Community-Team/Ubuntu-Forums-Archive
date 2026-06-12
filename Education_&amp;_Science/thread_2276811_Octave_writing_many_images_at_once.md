---
title: "Octave writing many images at once"
date: 2015-05-05
forum: Education &amp; Science
---

### Post by fevzi on 2015-05-05
[SIZE=2]I am using octave for my homework I need to read, process and write many images at once, I did the reading part but how do I write them as different images with different names. For example

```
for i=1:length (file)
    A = imread (file(i).name);
    B = imresize (A,[200 200]);
    imwrite (B," ? "); # Here is where I am stuck
end;
```

do I have to use an array of strings for the filename option in imwrite and index through those string, if so can you tell me how?





[/SIZE]

---

### Post by mJayk on 2015-10-06
Bit late you can iterate the strings 


[FONT=Verdana]for lmn = 1:length(file).[/FONT]
[FONT=Verdana]filename = ['OutputImage',num2str(lmn),'.ext'][/FONT]
A = imread (file(lmn).name);
    B = imresize (A,[200 200]);
    imwrite (B, filename); 
end;

---

