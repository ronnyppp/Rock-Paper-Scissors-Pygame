import pygame
import random
import time

pygame.init()

display_width = 800
display_height = 600
gameDisplay = pygame.display.set_mode((display_width, display_height))
pygame.display.set_caption("Rock, Paper, Scissors by Roniel")

black = (0,0,0)
white = (255,255,255)
red = (200, 0, 0)
green = (0, 200, 0)

bright_red = (255, 0 ,0)
bright_green = (0,255,0)
clock = pygame.time.Clock()

player_choice = ("")
computer_choice = None


rocImg = pygame.image.load('rock.jpg')
papImg = pygame.image.load("paper.png")
sciImg = pygame.image.load("download (1).jpg")

score_value = 0
score_surface = None
def score_increase():
   global score_value, score_surface
   score_value += 1
   font = pygame.font.SysFont(None, 25)
   score_surface = font.render("Score: "+str(score_value), True, black)



rockPosition = rocImg.get_rect()
rockPosition.bottom = (display_width * 0.75)
rockPosition.left = (display_height * 0.06)

paperPosition = papImg.get_rect()
paperPosition.bottom = (display_width * 0.7)
paperPosition.left = (display_height * 0.55)

scissorPosition = sciImg.get_rect()
scissorPosition.bottom = (display_width * 0.77)
scissorPosition.left = (display_height * 0.9)
def rock():
   gameDisplay.blit(rocImg, rockPosition)
def paper():
   gameDisplay.blit(papImg, paperPosition)
def scissors():
   gameDisplay.blit(sciImg, scissorPosition)

font = pygame.font.Font('freesansbold.ttf', 20)
text = font.render('Choose rock, paper or scissors. Try to beat the computer.', True, black, white)
textRect = text.get_rect()
textRect.center = ((display_width / 2), (display_height / 2))

def message_display(text):
   newFont = pygame.font.Font('freesansbold.ttf', 150)
   winText = newFont.render('You win!!!', True, black, white)
   winTextRect = winText.get_rect()
   winTextRect.center = ((display_width / 2), (display_height / 2))
   gameDisplay.blit(winText, winTextRect)
   pygame.display.update()
   time.sleep(2)
   game_loop()
def win():

   message_display("You win!!!")



def losemesssage_display(text):
   newFont = pygame.font.Font('freesansbold.ttf', 150)
   loseText = newFont.render('You lose :(', True, black, white)
   loseTextRect = loseText.get_rect()
   loseTextRect.center = ((display_width / 2), (display_height / 2))
   gameDisplay.blit(loseText, loseTextRect)
   pygame.display.update()
   time.sleep(2)
   game_loop()
def lose():
   losemesssage_display("You lost :(")
def tmessage_display(text):
   newFont = pygame.font.Font('freesansbold.ttf', 150)
   tieText = newFont.render('You tied :/', True, black, white)
   tieTextRect = tieText.get_rect()
   tieTextRect.center = ((display_width / 2), (display_height / 2))
   gameDisplay.blit(tieText, tieTextRect)
   pygame.display.update()
   time.sleep(2)
   game_loop()
def tie():
   tmessage_display("You tied :/")
def button(msg,x,y,w,h,ic,ac, action=None):
   mouse = pygame.mouse.get_pos()
   click = pygame.mouse.get_pressed()

   if x + w > mouse[0] > x and y + h > mouse[1] > y:
       pygame.draw.rect(gameDisplay, ac, (x, y, w, h))
       if click[0] == 1 and action != None:
           action()
   else:
       pygame.draw.rect(gameDisplay, ic, (x, y, w, h))
   playFont = pygame.font.Font('freesansbold.ttf', 40)
   playText = playFont.render(msg, True, black)
   playTextRect = playText.get_rect()
   playTextRect.center = ((x + (w / 2)), (y + (h / 2)))
   gameDisplay.blit(playText, playTextRect)
def quit_game():
   pygame.quit()
   quit()
def game_intro():
   intro = True
   while intro:
       for event in pygame.event.get():
           if event.type == pygame.QUIT:
               pygame.quit()
               quit()

       gameDisplay.fill(white)
       newFont = pygame.font.Font('freesansbold.ttf', 70)
       introText = newFont.render('Rock, Paper, Scissors', True, black, white)
       introTextRect = introText.get_rect()
       introTextRect.center = ((display_width / 2), (display_height / 2))
       gameDisplay.blit(introText, introTextRect)

       button("Start", 100, 420, 170, 70, green, bright_green, game_loop)
       button("Quit", 500, 420, 170, 70, red, bright_red, quit_game)



       pygame.display.update()
       clock.tick(15)

def game_loop():
   computer_choice = random.choice(["r", "p", "s"])


   while True:
       gameDisplay.fill(white)
       gameDisplay.blit(text, textRect)
       rock()
       paper()
       scissors()
       score_surface = font.render("Score: " + str(score_value), True, (0,0,0))
       if score_surface:
           gameDisplay.blit(score_surface,(0,0))



       def is_win(player, opponent):
           if (player == 'r' and opponent == 's') or (player == 's' and opponent == 'p') \
                   or (player == 'p' and opponent == 'r'):
               return True


       for event in pygame.event.get():

           if event.type == pygame.QUIT:
               pygame.quit()
               quit()
           elif event.type == pygame.MOUSEMOTION:
               x, y = event.pos


           elif event.type == pygame.MOUSEBUTTONDOWN:
               if rockPosition.collidepoint(event.pos):
                   player_choice = ("r")
                   if player_choice == computer_choice:
                       tie()
                   if is_win(player_choice, computer_choice):
                       score_increase()
                       win()
                   lose()
               elif paperPosition.collidepoint(event.pos):
                   player_choice = ("p")
                   if player_choice == computer_choice:
                       tie()
                   if is_win(player_choice, computer_choice):
                       score_increase()
                       win()
                   lose()
               elif scissorPosition.collidepoint(event.pos):
                   player_choice = ("s")
                   if player_choice == computer_choice:
                       tie()
                   if is_win(player_choice, computer_choice):
                       score_increase()
                       win()
                   lose()

           pygame.display.flip()
           clock.tick(60)
game_intro()
game_loop()
