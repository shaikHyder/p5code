# p5code


function setup() {
  createCanvas(1000, 600);
  background(245);
  textFont('Arial');
  noLoop();
  drawScene();
}

function drawScene() {
  drawBase();

  // Main objects
  drawRobot(150, 420);
  drawDrone(250, 200);
  drawSuspect(700, 430);
  drawDetectionUnit(500, 150);
  drawControlRoom(750, 120);
  drawPoliceUnit(750, 270);

  // Labels
  drawLabel("Robot", 150, 490, color(0));
  drawLabel("Drone", 250, 170, color(80));
  drawLabel("Suspicious Person", 700, 500, color(200, 0, 0));
  drawLabel("Detection System", 500, 230, color(255, 100, 0));
  drawLabel("Control Room", 750, 200, color(0, 100, 200));
  drawLabel("Police", 750, 360, color(0, 0, 150));

  // Arrows with SIMPLE text and spaced labels
  drawArrowWithSimpleText(150, 400, 250, 220, "Robot", "Drone");
  drawArrowWithSimpleText(250, 220, 700, 410, "Drone", "Suspect");
  drawArrowWithSimpleText(250, 220, 500, 170, "Drone", "Detection");
  drawArrowWithSimpleText(500, 170, 750, 140, "Detection", "Control");
  drawArrowWithSimpleText(500, 170, 750, 290, "Detection", "Police");
  drawArrowWithSimpleText(150, 400, 750, 290, "Robot", "Police");
}

function drawBase() {
  stroke(180);
  noFill();
  rect(50, 50, 900, 500, 20);
  fill(0);
  textSize(20);
  textAlign(CENTER);
  text("PATROL ROBOT + DRONE SIMPLE MONITORING DIAGRAM", width / 2, 80);
}

// --- Components ---

function drawRobot(x, y) {
  fill(180);
  stroke(0);
  rect(x, y, 80, 50, 10);
  fill(50);
  ellipse(x + 15, y + 50, 20);
  ellipse(x + 65, y + 50, 20);
  fill(0);
  ellipse(x + 40, y - 10, 20);
}

function drawDrone(x, y) {
  fill(120);
  stroke(0);
  ellipse(x, y, 40, 20);
  line(x - 20, y, x - 35, y - 15);
  line(x + 20, y, x + 35, y - 15);
  ellipse(x - 35, y - 15, 8);
  ellipse(x + 35, y - 15, 8);
}

function drawSuspect(x, y) {
  fill(0);
  ellipse(x, y - 20, 20);
  line(x, y - 10, x, y + 20);
  line(x - 15, y, x + 15, y);
  line(x, y + 20, x - 10, y + 40);
  line(x, y + 20, x + 10, y + 40);
}

function drawDetectionUnit(x, y) {
  fill(255, 150, 0, 100);
  stroke(0);
  rect(x - 60, y, 120, 60, 10);
  fill(0);
  textSize(12);
  textAlign(CENTER);
  text("AI Detector", x, y + 35);
}

function drawControlRoom(x, y) {
  fill(0, 150, 255, 100);
  stroke(0);
  rect(x, y, 120, 60, 10);
  fill(0);
  textSize(12);
  textAlign(CENTER);
  text("Control Room", x + 60, y + 35);
}

function drawPoliceUnit(x, y) {
  fill(0, 0, 200, 100);
  stroke(0);
  rect(x, y, 120, 60, 10);
  fill(255);
  textSize(12);
  textAlign(CENTER);
  text("Police Station", x + 60, y + 35);
}

function drawLabel(txt, x, y, col) {
  fill(col);
  noStroke();
  textSize(14);
  textAlign(CENTER);
  text(txt, x, y);
}

// --- Arrows with SIMPLE labels: "From X → To Y" ---
function drawArrowWithSimpleText(x1, y1, x2, y2, fromLabel, toLabel) {
  stroke(0);
  strokeWeight(2);
  line(x1, y1, x2, y2);

  // Arrowhead
  let angle = atan2(y2 - y1, x2 - x1);
  push();
  translate(x2, y2);
  rotate(angle);
  fill(0);
  noStroke();
  triangle(0, 0, -10, -5, -10, 5);
  pop();

  // Text offset to avoid overlap
  let mx = (x1 + x2) / 2;
  let my = (y1 + y2) / 2;

  fill(0);
  noStroke();
  textSize(11);
  textAlign(CENTER);
  text("From " + fromLabel, mx, my - 15);
  text("To " + toLabel, mx, my);
}
