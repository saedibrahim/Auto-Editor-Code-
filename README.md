# Auto-Editor-Code-
Auto Editor Code  is a program to catch the overused word in any document and highlight it 
function findText(item) {

//generate a random colors and save it in a variable to use as highlight color 
//credit to James from  https://stackoverflow.com/questions/1484506/random-color-generator
var background = '#' + (Math.random().toString(16) + "000000").substring(2,8)

//add the parameter to the log to test it is working as expected
Logger.log(item)


//creat the variable to show the result of finiding the  text
 var searchResult

//search for the text stored in the item variable
 searchResult = DocumentApp.getActiveDocument().getBody().findText(item)

//log the result of the research for testing
 Logger.log(searchResult)
 
 //while the sereach results for very are not empty do the following
 
 while (searchResult !==null){
 
 //change the background color of the research result text to  red
 searchResult.getElement().asText().setBackgroundColor(searchResult.getStartOffset(), searchResult.getEndOffsetInclusive(), background)
 
 //find the text again is stored in the item variable
 searchResult = DocumentApp.getActiveDocument().getBody().findText(item,searchResult)
 
 //end the loop 
 }
 
}



function highlightProblem() {

//creat an array to store all words that you will search for
var word = ["very", " so ", "So "," so","its", "totally", "really", "to", "alot"]

//find each item in the array
word.forEach(findText)

///the below piece of code is deleted as the word.forEach oiece of code play his role

//highlight the word very
 // findText("very")
  
  //highlight the word totally
  //findText("totally")

}
 
 //when document open add a custom menue that the highlight problem function 
function onOpen(){
 DocumentApp.getUi().createMenu("Make the writting awesome!").addItem("Highlight Common Mistake","highlightProblem").addToUi()




} 
 

 
 
 
 
 
 
 
 
 
