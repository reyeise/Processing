import java.util.Random;


class Leaf{
  
  PImage img; 
  Vector2 position;
  Vector2 velocity;
  Vector2 acc;
  Vector2 size;
  int mass = 10;
  int rotateDir = 1;

  int angle = 0;

  Boolean isTouchGround = false;
  Random rand = new Random();

  public Leaf(){
    this.position = randomPosition();
    this.velocity = new Vector2();
    this.acc = new Vector2();

    size = new Vector2(64,64);
    
    img = loadImage("leaf1.png"); 
    img.resize((int)size.getX(),(int)size.getY()); 
    
    
    if(rand.nextInt(2) == 1){
      rotateDir *= -1;
    }
    
  }
  public Leaf(Vector2 p){
    this.position = p;
    this.velocity = new Vector2();
    this.acc = new Vector2();

    size = new Vector2(64,64);
    
    img = loadImage("leaf1.png"); 
    img.resize((int)size.getX(),(int)size.getY()); 
  }
  


  
  public void update(){
    
    movement();
    touchGround();
  }

  void touchGround(){
    if (position.y > 720 - 32) {
      velocity.y *= -0.1; 
      isTouchGround = true;
      position.y = 720-32;
    }
  }
  
  public void movement()
  {
    if(isTouchGround){
      return;
    }
    
    
    
    velocity = velocity.add(acc);
    position = position.add(velocity);
    acc =  acc.mul(new Vector2(0,0));
  }
  
   void applyForce(Vector2 force) {
    Vector2 f = force.div(new Vector2(mass,mass));
    acc = acc.add(f);
    
  }

  
  Vector2 randomPosition(){
       
       double randY = -50 + Math.random() * (-10 + 50);
       Vector2 randPos = new Vector2(rand.nextInt(1280),(float)randY);
       return randPos;
  }
  
  
  public void draw(){
     //size(100, 100, P3D);
   // translate(width/2, height/2);
    //rotate(radians(60));
    //rect(position.getX(), position.getY(), 52, 52);
    pushMatrix();
    translate(this.position.getX(), this.position.getY());
    if(!isTouchGround){
       rotate(radians(angle));
    }
    rectMode(CENTER);
    image(img,0,0, 32, 32);
    popMatrix();
    
    angle += 5 * rotateDir;

    

  }
}
