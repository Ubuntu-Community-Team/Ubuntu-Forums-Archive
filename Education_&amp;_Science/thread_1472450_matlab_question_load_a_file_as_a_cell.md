---
title: "matlab question: load a file as a cell"
date: 2010-05-04
forum: Education &amp; Science
---

### Post by lethalfang on 2010-05-04
I'm wondering if anyone has a way to do this in matlab.

Say I have the following .txt file:
----------------------------
1 1 1 1 1
2 2 2 2 2
3 3 3 3
4 4 4 4
5 5 5 5
6 6 6 6
7 7 7 7 7 7 7 7
8 8 8 8 8 8 8 8
----------------------------

Is there a simple way to load this file as a cell, such that
cell{1} =
1 1 1 1 1
2 2 2 2 2

cell{2} =
3 3 3 3
4 4 4 4

cell{3} =
5 5 5 5
6 6 6 6

cell{4} =
7 7 7 7 7 7 7 7
8 8 8 8 8 8 8 8


So far, the only way I can think of is to write a bash script that converts that file into 4 separate files, and then load each of them separately.

Thanks in advance!

Li Tai

---

### Post by lethalfang on 2010-05-06
> **lethalfang said:**
> I'm wondering if anyone has a way to do this in matlab.

Say I have the following .txt file:
----------------------------
1 1 1 1 1
2 2 2 2 2
3 3 3 3
4 4 4 4
5 5 5 5
6 6 6 6
7 7 7 7 7 7 7 7
8 8 8 8 8 8 8 8
----------------------------

Is there a simple way to load this file as a cell, such that
cell{1} =
1 1 1 1 1
2 2 2 2 2

cell{2} =
3 3 3 3
4 4 4 4

cell{3} =
5 5 5 5
6 6 6 6

cell{4} =
7 7 7 7 7 7 7 7
8 8 8 8 8 8 8 8


So far, the only way I can think of is to write a bash script that converts that file into 4 separate files, and then load each of them separately.

Thanks in advance!

Li Tai



Ahh, well, I got an answer on mathworks newsgroup:

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%


% Read the file to a cell string:
Data_Raw = dataread('file', 'YourFileName.txt', '%s', 'delimiter', '\n');

N = size(Data_Raw,1) / 2;


% Split cell string to cells:
Data_Cell = cell(1, N); % Pre-allocate


for i = 1 : N

    Data_Cell{i} = [sscanf(Data_Raw{2*i-1}, '%f')'; sscanf(Data_Raw{2*i}, '%f')'];

end
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

---

