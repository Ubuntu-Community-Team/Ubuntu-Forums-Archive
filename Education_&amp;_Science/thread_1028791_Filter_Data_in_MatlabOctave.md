---
title: "Filter Data in Matlab/Octave"
date: 2009-01-02
forum: Education &amp; Science
---

### Post by in_flu_ence on 2009-01-02
I have an output as follows

E.g
output=[Time1 Data1 Count1
        Time1 Data2 Count2
        Time1 Data3 Count3
        Time2 Data1 Count1
        Time2 Data2 Count2
        Time2 Data3 Count3
        Time3 Data1 Count1
        Time3 Data2 Count2
        Time3 Data3 Count3]

How can I filter my data and just having an output1 only with rows having Count3?
i.e.
output1=[Time1 Data3 Count3
         Time2 Data3 Count3
         Time3 Data3 Count3]?

Thanks

---

### Post by stumbleUpon on 2009-01-03
> **in_flu_ence said:**
> I have an output as follows

E.g
output=[Time1 Data1 Count1
        Time1 Data2 Count2
        Time1 Data3 Count3
        Time2 Data1 Count1
        Time2 Data2 Count2
        Time2 Data3 Count3
        Time3 Data1 Count1
        Time3 Data2 Count2
        Time3 Data3 Count3]

How can I filter my data and just having an output1 only with rows having Count3?
i.e.
output1=[Time1 Data3 Count3
         Time2 Data3 Count3
         Time3 Data3 Count3]?

Thanks

[SIZE="4"]
[nrows ncols]=size(output);

output1 = output(3:3:nrows, 1:ncols)[/SIZE]

---

### Post by jpkotta on 2009-01-03
```
idx = find((output(:,3) == Count3));
output_filtered = output(idx,:);
```

---

