

import random
import re

WORDLIST_FILENAME = "words.txt"

def loadWords():
    inFile = open('words.txt', 'r')
    line = inFile.readline()
    wordlist = line.split()
    return wordlist

def chooseWord(wordlist):
    return random.choice(wordlist)


def hangman(secretWord):
    wordlist = loadWords()
    secretWord=chooseWord(wordlist)
    wordlength=len(secretWord)
    oppo=8
    elements=['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
    guessed=list("_" * wordlength)
    print('Welcome to the game Hangman!')
    print('I am thinking of a word is ' + str(wordlength) + " letters long")
    print('-----------')
    lettersGuessed=[]
    flag = True
    while flag==True:
        if oppo >= 1 :
            print("You have "+ str(oppo)+ " guesses left")
            print("Available letters: " + ''.join(elements))
            one_lettersGuessed=str(input("Please guess a letter:"))
            if one_lettersGuessed not in lettersGuessed:
                if one_lettersGuessed in secretWord:
                    lettersGuessed.append(one_lettersGuessed)
                    elements.remove(one_lettersGuessed)
                    ind=[m.start() for m in re.finditer(one_lettersGuessed, secretWord)]
                    for i in ind:
                        guessed[i]=one_lettersGuessed
                    print('Good guess:'+ ' '.join(guessed))
                    print('-----------')
                    if "_" in guessed:
                        flag=True
                    else:
                        print('Congratulations, you won!')
                        flag=False
                else:
                    lettersGuessed.append(one_lettersGuessed)
                    elements.remove(one_lettersGuessed)
                    oppo -= 1
                    print("Oops! That letter is not in my word: "+' '.join(guessed))
                    print('-----------')
            else:
                print("Oops! You've already guessed that letter: " +' '.join(guessed))
                print('-----------')

        else:
            print("Sorry, you ran out of guesses. The word was "+ str(secretWord) )
            flag = False

wordlist=loadWords()
secretWord = chooseWord(wordlist).lower()
hangman(secretWord)
