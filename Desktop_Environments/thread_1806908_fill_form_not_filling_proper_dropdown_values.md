---
title: "fill_form not filling proper dropdown values"
date: 2011-07-18
forum: Desktop Environments
---

### Post by pallavi@inc10.com on 2011-07-18
i am using the below code to create FDF file through pdf form 

function createFDF($file,$info){
    $data="%FDF-1.2\n%âãÏÓ\n1 0 obj\n<< \n/FDF << /Fields [ ";
    foreach($info as $field => $val){
    	if(is_array($val)){
        	$data.='<</T('.$field.')/V[';
        	foreach($val as $opt)
        		$data.='('.trim($opt).')';
        	$data.=']>>';
    	}else{
        	$data.='<</T('.$field.')/V('.trim($val).')>>';
    	}
    }
    $data.="] \n/F (".$file.") /ID [ <".md5(time()).">\n] >>".
        " \n>> \nendobj\ntrailer\n".
        "<<\n/Root 1 0 R \n\n>>\n%%EOF\n";
    return $data;
}

and pdftek command to create pdf from FDF file

pdftk pdftest.pdf fill_form $inputfile output $ouputfile
the value in fdf file is correct but not in created pdf file from it.

---

