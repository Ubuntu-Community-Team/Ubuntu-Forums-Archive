---
title: "no xml on kde"
date: 2006-02-15
forum: Desktop Environments
---

### Post by songo on 2006-02-15
hi..
i'm not able to see xml with konqueror.

eg, the result of the ballot.xml is:

XML parsing error
fatal parsing error: invalid name for processing instruction in line 45, column 6
<?xml version="1.0" encoding="ISO-8859-1"?>
     ^

ballot.xml
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- General ballot example -->

<ballot electionCode="1">
     <ballotDescription>
          <line>Example ballot</line>
          <line>Extra line</line>
          <!-- more lines -->
     </ballotDescription>
     <group code="1" description="Simple questions types"> 
          <!--type tag can have the values Single, Multiple, OpenS or OpenM-->     
          <question code="1" type="Single"> 
               <questionDescription>Is REVS robust?</questionDescription>
               <answer code="1">Yes</answer>
               <answer code="2">No</answer>
               <answer code="3">Don't know</answer>
          </question>
          <question code="2" type="Multiple"> 
               <questionDescription>Do you plan to use REVS in:</questionDescription>
               <answer code="1">National elections</answer>
               <answer code="2">Opinion surveys</answer>
               <answer code="3">Student elections</answer>
               <!-- more answers -->
          </question>
          <!-- more questions -->
     </group>
     <group code="2" description="Open questions types"> 
          <question code="1" type="OpenS"> 
               <questionDescription>What is your favorite color?</questionDescription>
               <answer code="1">Red</answer>
               <answer code="2">Green</answer>
               <answer code="3">Yellow</answer>
      <!-- more answers -->
          </question>
          <question code="2" type="OpenM"> 
               <questionDescription>What do you like to do in your free time?</questionDescription>
               <answer code="1">See a movie</answer>
               <answer code="2">Read a book</answer>
                    <!-- more answers -->
          </question>
          <!-- more questions -->
     </group>
     <!-- more groups -->
</ballot>

```

---

