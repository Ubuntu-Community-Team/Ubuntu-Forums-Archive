---
title: "Scilab  - Submatrix incorrectly defined"
date: 2010-05-19
forum: Education &amp; Science
---

### Post by krock4 on 2010-05-19
I am taking some code i created in matlab and trying to convert it to 
Scilab and am running into some issues: 
The code is below: 
clc 
clear 
worksheet = readxls('LTE101.xls'); 
worksheet2 = worksheet(2); 
SampNum = worksheet2.value(:,1);       
x = worksheet2.value(:,2);          
y = worksheet2.value(:,3);          
z = worksheet2.value(:,4);         
j=size(Speed);                    
Poly6=polyfit(x,y,6);      //Line of best fit 
Poly1(1)=Poly6(7); 
Poly1(2)=Poly6(6); 
Poly1(3)=Poly6(5); 
Poly1(4)=Poly6(4); 
Poly1(5)=Poly6(3); 
Poly1(6)=Poly6(2); 
Poly1(7)=Poly6(1); 
r=roots(Poly1) ;                  //Finds roots of 6th Degree 
Polynomial 
g=1; 
n=1; 
roots6a=zeros(40,2); 
[maxspeed,maxloc] = max(y); 
for(i=0:.25:x(maxloc))        //Loop that is going to find all roots 
from 0 to the max speed 
  Poly1(7)=Poly1-.25;             //of the stalker run 
  n=1; 
  c=Poly1; 
  rootchange = roots(c) 
  for m = 1:1:6 
    if((rootchange(m)> 0 && (rootchange(m)<(x(j(1))))) 
      if(rootchange(m) == real(rootchange(m))))            //Puts the real roots between 0 and the max
        roots6a(n,g) = rootchange(m)';  
      end 
    end 
  end 
  g=g+1; 
end 

I am creating a loop to find the exact x value from 0 to the max y. I tried using solve in matlab but it gave me a garbage forumla that does not work. My next step was to subtract .25 from the polynomial to find the roots because it will do the same thing. The code works fine in matlab and i have changed what i need to before the loop so finding the roots work. When i am in the loop i get an error saying "submatrix incorrectly defined". Does anyone know why this occuring? 

Thanks for your help
David

---

