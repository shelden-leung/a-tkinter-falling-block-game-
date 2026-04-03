# a-tkinter-falling-block-game-
#the project looked simple, but i learned how to makae and moddify shapes using tk, which is my second #game, #where i mastered the using of conditions and variables, and also creating multiple windows for a #scoreboard

#how to play
1.run the code
2. use 1, 2, 3 keys to move the character
3. try to catch the falling blocks coming while scoring as much as you can
4.enjoy





import tkinter as tk
import random
from tkinter import messagebox
from tkinter import simpledialog




                              
root = tk.Tk()
root.geometry("600x600")
wave = ["110", "250", "370"]
wave2 = ["110", "250", "370"]

sub_window = tk.Toplevel(root)
sub_window.title("score")
sub_window.geometry("400x300")



playerx = 250
choice = random.choice(wave)
wee = random.choice(wave2)
wv1 = int(choice)
wv2 = int(wee)
y = 1000
x = 800
score = 0
speed = 10


label_target = tk.Label(sub_window, text=f"Score: {score}", font=("Arial", 40))
label_target.pack(pady=100)




canvas = tk.Canvas(root, width=600, height=600, bg="white", highlightthickness=0)
canvas.pack()



bg_rect = canvas.create_rectangle(0, 0, 600, 600, fill="#97ffff")

rwall = canvas.create_rectangle(0, 0, 100, 600, fill="#8b5742")
lwall = canvas.create_rectangle(500, 0, 600, 600, fill="#8b5742")
wave1 = canvas.create_rectangle(wv1, y, wv1 + 100, y + 100, fill="blue")
wave2 = canvas.create_rectangle(wv2, x, wv2 + 100, x + 100, fill="blue")
player = canvas.create_rectangle(playerx, 10, playerx + 100, 110, fill="#32cd32")

       
def pos1(event):
    global playerx
    playerx = 110

def pos2(event):
    global playerx
    playerx = 250

def pos3(event):
    global playerx
    playerx = 370




34

root.bind("1", pos1)
root.bind("2", pos2)
root.bind("3", pos3)




def game_loop():
 global y, x, playerx, wv1, wv2, score, speed
 

 if True:
         y -= speed
         x -= speed

         


 if x == 110 and playerx == wv2 :
     x = 500
     score += 1
     label_target.config(text=f"Score: {score}")
     choice = random.choice(wave)
     wv2 = int(choice)

 if y == 110 and playerx == wv1:
     y = 500
     score += 1
     label_target.config(text=f"Score: {score}")
     choice = random.choice(wave)
     wv1 = int(choice)

     
     
 if x == 0 or y == 0:
     messagebox.showinfo("0", f"GAMEOVER, score: {score}")
     root.destroy()
     
 canvas.coords(player, playerx, 10, playerx + 100, 110)
 canvas.coords(wave1, wv1, y, wv1 + 100, y + 100)
 canvas.coords(wave2, wv2, x, wv2 + 100, x + 100)
 




 if True:
     root.after(50, game_loop)





game_loop()

root.mainloop()


