## Wordle in React

Data needed to be tracked:

* solution, a five letter string, `drain`
* past guesses
  * an array of past guesses
  * each past guess is an array of letter objects `[{}, {}, {}, {}, {}]`
  * each object represents a letter in the guess word `{key: 'a', color: 'yellow'}`
* current guess, which is a string `hello`
* keypad letters
  * an array of letter objects `[{key: 'a', color: 'green'}, {}, {} ...]`
* number of turns, which is an integer from `0` - `6`

Game process
* entering words:
  * user enterse a letter & a square is filled with that letter
  * when a user hits delete it deletes the previous letter
  * when a user hits enter it submits the word
    * if all squares are not filled with letters then the word is not submitted
    * if that word has already been used in a previous guess then the word is not submitted
* checking submitted words
  * each letter is checked to see if it matches to the solution
  * each letter is assigned a color based on its inclusion in the solution
    * exact matches (correct position in the solution) are green
    * partial matches (in the solution but not the correct position) are yellow
    * none-matches (no tin the solution at all) are grey
  * the guess is added to the grid with the correct colours
  * the current guess moves to the next row with the keypad letters are updated (colors)
* Ending the game
  * when the guessed word fully matches the solution
    * then modal to say 'well done'
  * when the user runs out of guesses then
    * modal to say 'unlucky'